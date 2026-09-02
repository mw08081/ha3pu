## 합격뿌수기 | 2025.01. ~ 2026.07. (개인프로젝트)

- 개요: 실시간 동영상 강의 스트리밍 서비스와 질문/소통 게시판 플랫폼

<br/>

- 기술 스택
    - Backend: Django, Node.js
    - Infra & DevOps:  GCP Compute Engine, Linux, Nginx, Gunicorn, Certbot(TLS), CloudFlare(Reverse Proxy)
    - Database: Google Cloud SQL (MySQL 8.0)
      
<br/>

- 상세 업무
    - VPC Private IP를 이용한 네트워크 홉 레이턴시 개선과 직렬화 오버헤드 및 1+N 쿼리 문제 해결을 통한 Django ORM 최적화로 데이터 용량 45% 절감 및 API 응답 속도 97% 개선
    - GCP, Nginx, Gunicorn, systemd 데몬 기반의 무중단 배포 환경구축 및 Certbot(TLS), CloudFlare(Reverse Proxy) 연동을 통한 HTTPS 보안 강화
    - Django 서버 토큰 기반 유저 인증/인가 시스템 구현 및 RESTful API 설계·개발
    - Node.js 및 HLS 프로토콜 기반 동영상 스트리밍 서버 구축과 Toss Payments PG 결제 모듈 연동


<br/>



## 기술 설명

<blockquote>
📣

구현 기술에 대한 주된 메커니즘들을 설명합니다

[1. 백엔드 아키텍처 및 성능 최적화](https://github.com/mw08081/ha3pu/blob/main/README.md#1-%EB%B0%B1%EC%97%94%EB%93%9C-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EB%B0%8F-%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94)

[2. 데이터베이스 설계 및 인덱싱 최적화](https://github.com/mw08081/ha3pu/blob/main/README.md#2-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%A4%EA%B3%84-%EB%B0%8F-%EC%9D%B8%EB%8D%B1%EC%8B%B1-%EC%B5%9C%EC%A0%81%ED%99%94)

[3. 인프라 및 네트워크 설계 ](https://github.com/mw08081/ha3pu/blob/main/README.md#3-%EC%9D%B8%ED%94%84%EB%9D%BC-%EB%B0%8F-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%84%A4%EA%B3%84)

[4. 시스템 및 인증 보안](https://github.com/mw08081/ha3pu/blob/main/README.md#4-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EB%B0%8F-%EC%9D%B8%EC%A6%9D-%EB%B3%B4%EC%95%88)

[5. HLS 기반 미디어 스트리밍 서버 분리 구축 및 토스페이먼츠 PG 연동](https://github.com/mw08081/ha3pu/blob/main/README.md#5-hls-%EA%B8%B0%EB%B0%98-%EB%AF%B8%EB%94%94%EC%96%B4-%EC%8A%A4%ED%8A%B8%EB%A6%AC%EB%B0%8D-%EC%84%9C%EB%B2%84-%EB%B6%84%EB%A6%AC-%EA%B5%AC%EC%B6%95-%EB%B0%8F-%ED%86%A0%EC%8A%A4%ED%8E%98%EC%9D%B4%EB%A8%BC%EC%B8%A0-pg-%EC%97%B0%EB%8F%99)

</blockquote>

<br/>

### 1. 백엔드 아키텍처 및 성능 최적화

#### 1) API 설계 및 DB 쿼리 최적화(select_related, annotate)

<blockquote>
🛠️

구현 목표

- 데이터 요청 지연 시간을 최소화하고, 서버 리소스 낭비를 방지하여 높은 데이터 처리 안정성을 확보한 백엔드 API 설계


<br/>

구현 내용

- **`select_related` 적용:** 주문(`Order`) 조회 시 연관된 상품(`Product`) 테이블을 `JOIN` 쿼리 한 번으로 함께 조회하도록 개선하여, 데이터 수에 비례해 DB 쿼리가 기하급수적으로 증가하는 1+N 문제 방지

<br/>

- **`annotate` 및 `Exists` 서브쿼리를 활용한 메모리 및 I/O 최적화:** 배송 정보 전체 객체를 메모리에 로드하는 대신, DB 엔진 레벨에서 존재 유무(`boolean`)만 판단하여 가져오도록 설계. 불필요한 데이터 전송량을 대폭 줄이고 직렬화(Serialization) 오버헤드 감소

```python
# select_related를 이용해 관련된 정보도 같이 가져옴으로써, 1+N 쿼리 문제를 해결
orders = Order.objects.select_related('product').annotate(
		# annotate를 이용해 배송 정보 존재 유무만 직렬화
    has_shipping=Exists(
        Shipping.objects.filter(order=OuterRef('pk'))
    )
)
```

<img width="1070" height="373" alt="Image" src="https://github.com/user-attachments/assets/e3be28f7-df72-46bb-a345-4f6260a151c6" />
참고자료

</blockquote>

#### 2) API 설계 및 DB 쿼리 최적화(F 객체)

<blockquote>
🛠️

구현 목표

- 재고 차감 및 수량 변경 시 발생하는 동시성 문제 방지 및 불필요한 Read-Before-Write 쿼리 최소화


<br/>

구현 내용

- 애플리케이션 메모리로 데이터를 조회(`SELECT`) 후 수정하여 다시 저장(`UPDATE`)하는 기존 방식 대신, DB 엔진 레벨에서 직접 컬럼 값을 참조하여 연산을 수행하도록 구현

<br/>

- 불필요한 `SELECT` 쿼리를 생략하고 단일 `UPDATE` 쿼리만 전송하여 데이터베이스와의 Round-Trip Time(RTT) 최소화

코드

```python
updated_count = Product.objects.filter(
    id=product_id, 
    stock_quantity__gte=1
).update(
    stock_quantity=F('stock_quantity') - 1
)

if updated_count == 0:
    raise OutOfStockException("재고가 부족합니다.")
```

</blockquote>

<br/>

### 2. 데이터베이스 설계 및 인덱싱 최적화

#### 1) DB 설계

<blockquote>
🛠️

구현 목표

- 정규화를 통해 데이터 중복을 최소화하고, 엔티티 간 무결성과 독립성을 확보한 데이터베이스 아키텍처 구축


<br/>

설계 방법

- **`User` - `Product` (N:M 해소 및 데이터 스냅샷 보장)**

`User`와 `Product` 간 다대다(N:M) 관계를 교차 테이블인 `Order`로 해소하고, 구매 시점의 가격(`final_price`)을 별도 보관하여 원본 상품 정보 변경에도 과거 결제 데이터의 무결성을 유지

<br/>

- `Order` - `Payment` ****(1:1 역할 분리 및 관심사 분리)

주문 본체 데이터와 PG 결제 데이터(`Payment`)를 `1:1 (OneToOneField)` 관계로 분리 설계하여, 결제 시도·실패·취소 등의 상태 변화 라이프사이클이 주문 본문 데이터를 오염시키지 않도록 관심사를 명확히 격리

<br/>

- **`Order` - `Shipipng`** (최소 권한 기반의 데이터 보안 및 조회 최적화)

배송 발주 시스템에서 최소한의 데이터 테이블을 검색하고, 거래처 계정에 `Shipping` 테이블 조회 권한만 제공함으로써 데이터 패킷 최적화와 데이터베이스 보안을 향상


<br/>

결과(일부 필드 생략) 
<img width="1000" height="662" alt="Image" src="https://github.com/user-attachments/assets/df682d69-aa53-4edc-ba95-6cee7ec16432" />

</blockquote>

#### 2) DB 인덱싱 최적화

<blockquote>
🛠️

구현 목표

- 빈번하게 발생하는 필터링·정렬 조건에 최적화된 인덱스를 구성하여, DB CPU 사용량 절감 및 쿼리 응답 속도 최적화


<br/>

구현 내용

- `User.email`,`Payment.payments_key` (`Unique Index`)
    - **설계 이유:** 고유 식별자 단건 조회 시  테이블 전체 검색을 방지하고 데이터 중복을 근본적으로 차단하기 위해 설정
    - **기대 효과:** O(1) 수준의 조회 속도 확보 및 데이터 유일성(Uniqueness) 제약 강제
    
    ```python
    class User(AbstractBaseUser, PermissionsMixin):
    		# 이메일 필드(필수, 검색)
        email = models.EmailField(
    		    unique=True
        )
        
    class Payment(models.Model):
        # 결제 키 필드(검색, 결제취소)
        payments_key = models.CharField(
            max_length=200,
            unique=True
        )
    ```
    

<br/>


- **`Order.purchase_date` (`db_index=True` 단일 인덱스)**
    - **설계 이유:** 특정 기간의 주문 내역 조회 및 최신순 정렬(`ORDER BY purchase_date DESC`) 쿼리가 빈번하게 발생하는 점을 고려하여 설정.
    - **기대 효과:** DB의 추가적인 메모리/CPU 정렬 연산을 제거하고, 기간 검색 범위를 최소화하여 읽기 성능 향상.
    
    ```python
    class Order(models.Model):
        purchase_date = models.DateTimeField(
            auto_now_add=True, 
            db_index=True
        )
    ```
    

<br/>


- **`Payment.payment_state` + `Payment.created_at` (`Composite Index` 복합 인덱스)**
    - **설계 이유:** "특정 상태(예: 결제 대기)인 데이터 중 특정 기간 내 작성된 건"을 필터링하는 조건 검색 패턴에 최적화하기 위해 설정
    - **기대 효과:** 단일 필드 인덱싱 시 발생하는 불필요한 레코드 스캔을 최소화하고, 결제 정산 및 상태 추적 배치(Batch) 쿼리 속도 극대화
    
    ```python
    class Payment(models.Model):
        STATE_CHOICES = [
            ('SUCCESS', '결제 완료'),
            ('WAITING_CANCEL', '취소 대기'),
            ('CANCELED', '취소 완료'),
        ]
        
        # 결제 상태 (결제 완료, 취소 대기, 취소 완료)
        payment_state = models.CharField(max_length=20, choices=STATE_CHOICES, default='SUCCESS')
        # 거래 일시
        created_at = models.DateTimeField(auto_now_add=True)
    
        class Meta:
            indexes = [
                # [복합 인덱스] 결제 상태별/기간별 내역 조회 최적화 (어드민 / 유저 결제 조회)
                models.Index(fields=['payment_state', 'created_at'], name='idx_pay_state_created'),
            ]
    ```
    
</blockquote>

<br/>

### 3. 인프라 및 네트워크 설계

<img width="791" height="355" alt="Image" src="https://github.com/user-attachments/assets/8076d6ed-1ce9-4b99-bc35-8d7b188777d2" />

#### 1) GCP 기반의 클라우드 인프라 구축

<blockquote>
🛠️

구현 목표

- GCP 생태계를 활용하여 컴퓨팅, DB, 스토리지를 분리함으로써 서비스의 가용성 확보하고 안정적인 서버 운영 환경 구축


<br/>

구현 내용

- Compute Engine: Linux OS 기반 서버 구축 및 외부 고정 IP(Static IP) 할당을 통한 안정적인 서버 엔드포인트 운용

<br/>

- Cloud SQL: MySQL 8.0 기반으로 애플리케이션 서버와 DB를 분리하고, VPC 내부 IP 연동을 통해 외부 무단 접근 차단 및 네트워크 홉(Hop) 감소로 데이터 통신 성능과 비용 최적화

<br/>

- Cloud Storage: 정적 자원 및 유저 미디어 파일을 GCS 버킷으로 격리하여 서버 I/O 부담을 해소하고, 프라이빗 버킷에서 서명된 URL(Signed URL) 방식을 적용해 파일 보안 및 권한 검증 처리를 GCP 서비스로 이관
</blockquote>

#### 2) 웹 서버 및 네트워크 아키텍처 최적화

<blockquote>
🛠️

구현 목표

- 클라이언트와 애플리케이션 간 보안성 강화 및 WSGI/Reverse Proxy 레이어 구성을 통한 웹 요청 처리 성능 최적화

<br/>

구현 내용

- Nginx & Gunicorn: Nginx를 Reverse Proxy로 두어 정적 파일 처리 및 SSL 종단을 담당하게 하고, Unix Socket 연동 기반의 Gunicorn(WSGI)을 통해 Django 애플리케이션으로의 요청 동시성 효율화

<br/>

- Cloud Flare: DNS 타깃팅 및 Reverse Proxy모드를 적용하여 원천 서버 IP 노출을 차단하고 DDoS 등 외부 보안 위협 1차 방어
</blockquote>

<br/>

### 4. 시스템 및 인증 보안

#### 1) Cloud SQL 데이터베이스 보안 및 감사 체계 구축

<blockquote>
🛠️

구현 목표

- 데이터베이스 레이어의 네트워크 격리, 전송 구간 암호화, 최소 권한 적용 및 감사 로그 체계를 구축하여 외부 데이터 침해 방지 및 시스템 추적성 강화

<br/>

구현 내용

- 비공개 IP 전용 구성: Cloud SQL을 VPC 내부 전용 IP로 전환하여 공용 인터넷 노출을 차단

<br/>

- 전송 구간 SSL/TLS 암호화 및 패킷 검증: `'ssl_mode': 'REQUIRED'` 옵션 적용

```python
'OPTIONS': {
      'charset': 'utf8mb4',
      'ssl': {
          'ssl_mode': 'REQUIRED'    # 데이터 전송 암호화 강제!
      }
},
```

```bash
sudo tcpdump -i any -X -vv port 3306

# 암호화 전
0x0240:  5f70 6466 1864 6f77 6e6c 6f61 645f 6578  _pdf.download_ex

# 암호화 후
0x0240:  b032 6a20 e1a7 d2b2 2431 e14f 2db3 e01b  .2j.....$1.O-...
```

<br/>

- 최소 권한 원칙(Principle of Least Privilege) 계정 관리: 기존 `root` 접속 방식에서 탈피하여 서비스 전용 최소 권한 계정(`django_user`)으로 DB 인가 권한 제한

<br/>

- GCP Cloud Audit Logging 감사 체계 구축: DB 감사 플래그(`cloudsql_mysql_audit = ON`) 및 IAM 연동을 설정하고 Log Explorer 쿼리를 활용한 DML 추적 환경 구성
    
<img width="533" height="341" alt="Image" src="https://github.com/user-attachments/assets/eb696098-d696-4514-80f5-e13b0ae0adfb" />

감사 플래스 설정 상태

<img width="1371" height="333" alt="Image" src="https://github.com/user-attachments/assets/52835067-c215-4b9b-90d6-ed20bca83f30" />

로그 탐색기에서 LQL 설정시 다음과 같은 내용을 확인할 수 있다 (현재 general_log를 통해서 검색)
    
</blockquote>

#### 2) Django 기본 토큰 기반 유저 인증

<blockquote>
🛠️

구현 목표

- Django 기본 TokenAuthentication 구조를 활용하여 API 요청별 사용자 접근 권한 검증 강화


<br/>

구현 내용

- Django TokenAuthentication 적용: 유저 로그인 시 서버 단에서 고유 Token을 발급·매핑하고, HTTP Header를 통한 요청 검증 처리

<br/>

- RESTful API 권한 제어: `@permission_classes([IsAuthenticated])`를 활용해 보호된 엔드포인트에 대한 무단 접근 차단


<br/>

코드

```python
# 로그인 시, 토큰 생성 및 조회 후 Response로 돌려줌

token, _ = Token.objects.get_or_create(user=user)
        
return Response(
    {
        'user_id': user.id, 'token': token.key 
    },
    status=status.HTTP_200_OK
)
```

```dart
// 웹에서 request 시, header에 토큰을 담아서 전송

final response = await http.get(
  Uri.https(ApiHelper.djangoServerApiAddr, '/user/getUser'),
  headers: {
    'Authorization': 'Token $token', // 토큰 헤더로 전달
  },
);
```

```python
# 해더의 인증 토큰을 파싱하여 인증된 유저의 요청만 response하도록 데코레이터 설정

@api_view(['GET'])
@permission_classes([IsAuthenticated])
def get_user(request):
		# ..기타 예외 처리 생략.. 

    # 헤더의 토큰으로 검증된 request.user 객체를 직렬화함
    serializer = UserSerializer(request.user)
    
    return Response(
        serializer.data,
        status=status.HTTP_200_OK
    )
```

</blockquote>

<br/>

### 5. HLS 기반 미디어 스트리밍 서버 분리 구축 및 토스페이먼츠 PG 연동

#### 1) Cloud SQL 데이터베이스 보안 및 감사 체계 구축

<blockquote>
🛠️

구현 목표

- 메인 웹 서버(Django)의 동영상 I/O 병목 현상을 방지하기 위해 비동기 처리 기반의 Node.js 스트리밍 전용 모듈 구축


<br/>

구현 내용

- Nginx 리버스 프록시 연동: 서브도메인으로 유입되는 HTTP 트래픽을 내부 HLS_SERVER_PORT 포트의 Node.js 서버로 전달하여 보안성 및 TLS 처리 분리

```bash
# 2. Nginx 설정 
server {
    server_name SUB_DOMAIN;

    location / {
        proxy_pass http://127.0.0.1:HLS_SERVER_PORT;
    }
}
```


<br/>

- GCS 비공개 버킷 스트림 연동: 로컬 디스크 저장 방식 대신 `@google-cloud/storage` SDK를 통해 GCS 버킷 내 HLS 파일 존재 여부(`exists`)를 검증하고, 읽기 스트림(`createReadStream`)을 생성하여 서버 메모리 점유 최소화

```jsx
// hls request 필터 및 파일 유무 확인
exists: async (req, cb) => {
    if (!req.url.endsWith('.m3u8') && !req.url.endsWith('.ts')) { //.. 생략}
    else {
		    // .. 중략
		    const [exists] = await storage.bucket(bucketName).file(filePath).exists();

	      if (exists) {
	        return cb(null, true); // 파일 유무 확인 후 플래그 반환
	      }
    }
}
```

```jsx
// .ts 파일 반환 과정
getSegmentStream: (req, cb) => {
  const filePath = req.url.substring(1); 
  const file = storage.bucket(bucketName).file(filePath); 
  const stream = file.createReadStream(); // 비동기 스트림 생성 (메모리 최적화)

  // .. 
  
  cb(null, stream);
}
```

</blockquote>

#### 2) 토스페이먼츠 PG 연동

<blockquote>
🛠️

구현 목표

- 클라이언트-서버 간 금액 검증으로 결제 데이터 위변조를 차단하고, 실패 시나리오별 예외 처리를 통해 결제 트랜잭션의 무결성과 안정성을 확보


<br/>

구현 내용

- 6번: 토스페이먼츠 API 스펙에 따라 결제 요청과 최종 승인(Confirm) 과정을 분리하여 처리
- 7번: 2번 과정에서 서버 DB에 저장한 주문 데이터(유저, 금액)와 6번에서 전달받은 결제 정보가 일치하는지 검증 (4번 클라이언트 단계에서의 금액 변조 차단)

<img width="606" height="521" alt="image 5" src="https://github.com/user-attachments/assets/4412eae2-96e5-48b4-9f99-6115a85d20f4" />  

ㅤ  

코드


```python
# get_payments_page 결제하기 버튼 클릭

@permission_classes([IsAuthenticated])
@xframe_options_exempt
def get_payments_page(request, orderID):
    try:
        context = {
						# 구매자 정보, 금액
        }
    # ..생략..

    return render(request, 'payments.html', context)
```

```jsx
// payments.html에서 requestPayment()를 호출

requestPayment();
      
async function requestPayment() {
        try {
          // ..requestPayment 준비과정 생략..
          
          await tossPayments.payment({
            customerKey,
          }).requestPayment({
            // .. 기타 파라메터 생략 ..
            amount,
            successUrl: successUrl.toString(), // 성공시 리다이렉트 될 주소 
            
```

```python
# 유저의 결제 요청과 함게 결제 성공 여부를 tosspayments api를 통해 확인

# 결제 성공 여부를 확정 짓는 API
@api_view(['POST'])
def confirm(request) :
    try:
       # 결제 유저 검증
       # 결제 금액 검증
       
        conn = http.client.HTTPSConnection("api.tosspayments.com")
        # payload 생성
       
        headers = {
            'Authorization': encrypted_secret_key,
            'Content-Type': "application/json"
        }
        conn.request("POST", "/v1/payments/confirm", payload_json, headers)

				
				# 이후 response 에서 결제 확인이 되면 
				# 결제 성공 비즈니스 로직을 실행
```

</blockquote>


<br/>
<br/>

### 트러블 슈팅

<blockquote>
📣

주요 트러블 슈팅에 관해서 설명합니다.

[1. 특정 조회 API 병목 개선 및 ORM 최적화(응답속도 97% 개선)](https://github.com/mw08081/ha3pu/blob/main/README.md#1-%ED%8A%B9%EC%A0%95-%EC%A1%B0%ED%9A%8C-api-%EB%B3%91%EB%AA%A9-%EA%B0%9C%EC%84%A0-%EB%B0%8F-orm-%EC%B5%9C%EC%A0%81%ED%99%94%EC%9D%91%EB%8B%B5%EC%86%8D%EB%8F%84-97-%EA%B0%9C%EC%84%A0)


[2. 토스페이먼츠 PG연동 간 발생한 CSRF 관련 웹 보안 문제](https://github.com/mw08081/ha3pu/blob/main/README.md#2-%ED%86%A0%EC%8A%A4%ED%8E%98%EC%9D%B4%EB%A8%BC%EC%B8%A0-pg%EC%97%B0%EB%8F%99-%EA%B0%84-%EB%B0%9C%EC%83%9D%ED%95%9C-csrf-%EA%B4%80%EB%A0%A8-%EC%9B%B9-%EB%B3%B4%EC%95%88-%EB%AC%B8%EC%A0%9C)


[3. 대용량 파일 처리 부하 개선: GCP Signed URL 기반 전송 책임 이관](
https://github.com/mw08081/ha3pu/blob/main/README.md#3-%EB%8C%80%EC%9A%A9%EB%9F%89-%ED%8C%8C%EC%9D%BC-%EC%B2%98%EB%A6%AC-%EB%B6%80%ED%95%98-%EA%B0%9C%EC%84%A0-gcp-signed-url-%EA%B8%B0%EB%B0%98-%EC%A0%84%EC%86%A1-%EC%B1%85%EC%9E%84-%EC%9D%B4%EA%B4%80)

</blockquote>

<br/>

### 1. 특정 조회 API 병목 개선 및 ORM 최적화(응답속도 97% 개선)

<blockquote>
🛠️

문제 상황

- 특정 조회 API 호출 시 응답 데이터 용량이 314KB에 달하고, 응답 시간이 3.0초까지 지연되는 심각한 성능 병목 현상 발생
- 데이터 처리 지연으로 인해 사용자 경험(UX) 저해 및 백엔드 서버 리소스 부담 가중


<br/>

**원인 분석 및 가설 검증** 

- 가설 1: GCP Compute Engine과 Cloud SQL 간 네트워크 홉 레이턴시
    - 검증: 최초 설정에서 두 인스턴스 모두 Public IP 환경이었기에 네트워크 홉 레이턴시를 의심하여 Public IP → VPC Private IP 환경으로 전환했으나 개선 미비 (인프라 이슈 배제)


- 가설 2: API 직렬화(Serialization) 과정에서의 오버헤드 및 1+N 쿼리 문제
    - 검증: 무분별하게 연결된 외래키 필드 제거 및 ORM 최적화(`select_related`, `annotate` 활용)를 통해 DB 레벨에서 최적화된 데이터만 추출하도록 수정

```python
# select_related를 이용해 관련된 정보도 같이 가져옴으로써, 1+N 쿼리 문제를 해결
orders = Order.objects.select_related('product').annotate(

		# annotate를 이용해 배송 정보 존재 유무만 직렬화
    has_shipping=Exists(
        Shipping.objects.filter(order=OuterRef('pk'))
    )
)
```

<img width="1070" height="373" alt="image" src="https://github.com/user-attachments/assets/80a3759e-dfdc-459e-9de8-644fc3120dec" />  

<br/>

ㅤ

결과 

- 데이터 용량 45% 절감 (314KB → 172KB), API 응답 속도 97% 개선 (3.0초 → 0.09초). DB-Application 간의 효율적인 데이터 흐름 설계 능력을 배양함
- 최적화된 ORM의 중요성과 메모리 점유로 인한 서버 부하를 실제로 체험해볼 수 있었음

</blockquote>

<br/>

### 2. 토스페이먼츠 PG연동 간 발생한 CSRF 관련 웹 보안 문제

<blockquote>
🛠️

문제 상황

- 토스페이먼츠 결제창 인증 완료 후, 백엔드 승인 엔드포인트(`/store/confirm`)로 `POST` 요청 전송 시 **`403 Forbidden (CSRF verification failed)`** 에러가 발생하며 결제 승인 실패.
- 세션 기반 인증이 적용된 백엔드 환경에서 결제 승인 요청이 보안 미들웨어에 의해 차단됨


<br/>

**원인 분석** 

- **헤더 누락:** `POST` 요청에 대해 브라우저 쿠키와 요청 헤더 CSRF 토큰을 교차 검증이 필요하지만, `X-CSRFToken` 헤더 누락으로 요청이 차단됨

```jsx
// 토스페이먼츠 결제 완료 후 리다이렉트된 payments_success.html의 스크립트

const response = await fetch(`${window.location.origin}/store/confirm`, {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "X-CSRFToken": csrftoken                // X-CSRFToken 헤더 추가하여 CSRF 검증 통과
  },
  credentials: "include",
  body: JSON.stringify(requestData),
});
```


<br/>

결과 

- 웹 보안 및 CSRF 방어 메커니즘 이해: 쿠키 기반 웹 애플리케이션에서 `POST` 요청 시 왜 CSRF 토큰 검증이 필요한지, 헤더와 쿠키 간 교차 검증 구조를 이해함
</blockquote>

<br/>

### 3. 대용량 파일 처리 부하 개선: GCP Signed URL 기반 전송 책임 이관

<blockquote>
🛠️

문제 상황

- 두가지 서비스가 몰릴 경우 대용량 I/O와 수많은 네트워크 커넥션 발생으로 인해 서버 자원에 극심한 병목과 부하 발생


<br/>

**원인 분석** 

- 단일 인프라 내 리소스 처리 병목: 동일 Compute Engine 인프라 자원을 공유하는 구조에서 Node.js의 지속적인 HLS 조각 파일 스트리밍 요청과 Django 서버의 대용량 파일 다운로드 I/O가 동시에 몰려 CPU 및 Disk I/O 병목이 심화됨


<br/>

시도

- HLS 전용 Compute Engine 인스턴스 추가: HLS 서버를 다른 Comput Engine Instance로 분리하는 방법도 고민해봤지만, 클라우드 서비스 비용 부담 증가로 무리가 있음을 확인


<br/>

해결 방법

- GCP Cloud Storage Signed URL 도입: 클라이언트는 전달받은 Signed URL을 이용해 GCS에서 직접 파일 다운로드

```python
def download_file(request, file_path):
		# 유저 인증 및 다운로드 가능 여부 검증
   
    # 서명된 URL 생성
    signed_url = generate_signed_url(GCS_BUCKET_NAME , file_path)
    
    # 사용자를 GCS로 리다이렉트
    return HttpResponseRedirect(signed_url)
```

```python
def generate_signed_url(bucket_name, file_path, expiration=10):
    # 파일 검색 및 url 생성 준비

    # 서명된 URL 생성
    return blob.generate_signed_url(
        version="v4",
        expiration=timedelta(seconds=expiration),
        method="GET",
        response_disposition=(
            f'attachment; filename="{file_label}.{blob_extension}"; filename*=UTF-8\'\'{quote(file_label + "." + blob_extension)}'
        )
    )
```


<br/>

결과 

- Compute Engine 부하 감소 : 대용량 파일 다운로드 책임을 GCS 인프라로 완전히 넘김으로써 Gunicorn Worker 스레드 점유와 Disk I/O 병목을 근본적으로 해결
- 보안성과 효율성의 양립: 다운로드 Url에 유효기간 방식을 더해 추가적인 보안성을 확보
</blockquote>
