<html><head><meta http-equiv="Content-Type" content="text/html; charset=utf-8"/><title>포트폴리오</title><style>
/* cspell:disable-file */
/* webkit printing magic: print all background colors */
html {
	-webkit-print-color-adjust: exact;
}
* {
	box-sizing: border-box;
	-webkit-print-color-adjust: exact;
}

html,
body {
	margin: 0;
	padding: 0;
}
@media only screen {
	body {
		margin: 2em auto;
		max-width: 900px;
		color: rgb(55, 53, 47);
	}
}

body {
	line-height: 1.5;
	white-space: pre-wrap;
}

a,
a.visited {
	color: inherit;
	text-decoration: underline;
}

.pdf-relative-link-path {
	font-size: 80%;
	color: #444;
}

h1,
h2,
h3 {
	letter-spacing: -0.01em;
	line-height: 1.2;
	font-weight: 600;
	margin-bottom: 0;
}

/* Override strong tags inside headings to maintain consistent weight */
h1 strong,
h2 strong,
h3 strong {
	font-weight: 600;
}

.page-title {
	font-size: 2.5rem;
	font-weight: 700;
	margin-top: 0;
	margin-bottom: 0.75em;
}

h1 {
	font-size: 1.875rem;
	margin-top: 1.875rem;
}

h2 {
	font-size: 1.5rem;
	margin-top: 1.5rem;
}

h3 {
	font-size: 1.25rem;
	margin-top: 1.25rem;
}

.source {
	border: 1px solid #ddd;
	border-radius: 3px;
	padding: 1.5em;
	word-break: break-all;
}

.callout {
	border-radius: 10px;
	padding: 1rem;
}

/* For default-background callouts, render the border outline. */
.callout.block-color-default_background {
	border: 1px solid rgba(55, 53, 47, 0.09);
}

figure {
	margin: 1.25em 0;
	page-break-inside: avoid;
}

/*
 * Toggles and callouts hold arbitrary content, so they can easily be taller
 * than a page. They must stay breakable: avoiding breaks inside them makes
 * Chromium push the whole block onto the next page, which leaves the previous
 * page mostly empty before every long toggle.
 */
details,
aside {
	margin: 1.25em 0;
}

/* Keep a toggle's title on the same page as the start of its content. */
summary {
	page-break-after: avoid;
	break-after: avoid;
}

/*
 * Toggle headings render as <h1/h2/h3 style="display:inline-block"> inside
 * <summary>. Without this reset, the heading's margin-top pushes it below the
 * ::marker (▼), so the triangle and the title appear on separate lines.
 */
summary h1,
summary h2,
summary h3,
summary h4 {
	margin-top: 0;
}

figcaption {
	opacity: 0.5;
	font-size: 85%;
	margin-top: 0.5em;
}

mark {
	background-color: transparent;
}

.indented {
	padding-left: 1.5em;
}

hr {
	background: transparent;
	display: block;
	width: 100%;
	height: 1px;
	visibility: visible;
	border: none;
	border-bottom: 1px solid rgba(55, 53, 47, 0.09);
}

img {
	max-width: 100%;
}

@media only print {
	img {
		max-height: 100vh;
		object-fit: contain;
	}

	table.collection-content {
		width: 100%;
		table-layout: fixed;
	}

	table.collection-content th,
	table.collection-content td {
		overflow-wrap: anywhere;
	}

	table.collection-content td > .user,
	table.collection-content td > time {
		white-space: pre-wrap;
	}
}

@page {
	margin: 1in;
}

.collection-content-wrapper {
	overflow-x: auto;
}

@media only print {
	.collection-content-wrapper {
		overflow-x: visible;
	}
}

.collection-content {
	font-size: 0.875rem;
}

.collection-content td {
	white-space: pre-wrap;
	word-break: break-word;
}

.column-list {
	display: flex;
	gap: 46px;
}

.column {
	min-width: 0;
	overflow: hidden;
}

.column > *:first-child {
	margin-top: 0;
}

.table_of_contents-item {
	display: block;
	font-size: 0.875rem;
	line-height: 1.3;
	padding-inline: 0.125rem;
	padding-block: 0.375rem;
}

.table_of_contents-indent-1 {
	margin-left: 1.5rem;
}

.table_of_contents-indent-2 {
	margin-left: 3rem;
}

.table_of_contents-indent-3 {
	margin-left: 4.5rem;
}

.table_of_contents-link {
	text-decoration: none;
	opacity: 0.7;
	border-bottom: 1px solid rgba(55, 53, 47, 0.18);
}

table,
th,
td {
	border: 1px solid rgba(55, 53, 47, 0.09);
}

table {
	border-collapse: collapse;
	border-left: none;
	border-right: none;
}

th,
td {
	font-weight: normal;
	padding: 0.25em 0.5em;
	line-height: 1.5;
	min-height: 1.5em;
	text-align: left;
}

th {
	color: rgba(55, 53, 47, 0.6);
}

ol,
ul {
	margin: 0;
	margin-block-start: 0.6em;
	margin-block-end: 0.6em;
}

li > ol:first-child,
li > ul:first-child {
	margin-block-start: 0.6em;
}

ul > li {
	list-style: disc;
}

ul.to-do-list {
	padding-inline-start: 0;
}

ul.to-do-list > li {
	list-style: none;
}

.to-do-children-checked {
	text-decoration: line-through;
	opacity: 0.375;
}

ul.toggle > li {
	list-style: none;
}

ul {
	padding-inline-start: 1.7em;
}

ul > li {
	padding-left: 0.1em;
}

ol {
	padding-inline-start: 1.6em;
}

ol.numbered-list.numbered-list-digits-2 {
	padding-inline-start: 2em;
}

ol.numbered-list.numbered-list-digits-3plus {
	padding-inline-start: 2.4em;
}

ol > li {
	padding-left: 0.2em;
}

.mono ol {
	padding-inline-start: 2em;
}

.mono ol > li {
	text-indent: -0.4em;
}

.toggle {
	padding-inline-start: 0em;
	list-style-type: none;
}

/* Indent toggle children */
.toggle > li > details {
	padding-left: 1.7em;
}

.toggle > li > details > summary {
	margin-left: -1.1em;
}

.selected-value {
	display: inline-block;
	padding: 0 0.5em;
	background: rgba(206, 205, 202, 0.5);
	border-radius: 3px;
	margin-right: 0.5em;
	margin-top: 0.3em;
	margin-bottom: 0.3em;
	white-space: nowrap;
}

.collection-title {
	display: inline-block;
	margin-right: 1em;
}

.page-description {
	margin-bottom: 2em;
}

.simple-table {
	margin-top: 1em;
	font-size: 0.875rem;
	empty-cells: show;
}
.simple-table td {
	height: 29px;
	min-width: 120px;
}

.simple-table th {
	height: 29px;
	min-width: 120px;
}

.simple-table-header-color {
	background: rgb(247, 246, 243);
	color: black;
}
.simple-table-header {
	font-weight: 500;
}

time {
	opacity: 0.5;
}

.icon {
	display: inline-flex;
	align-items: center;
	justify-content: center;
	max-width: 1.2em;
	max-height: 1.2em;
	text-decoration: none;
	vertical-align: text-bottom;
	margin-right: 0.5em;
}

/*
 * Render emoji icons using a ::before pseudo-element to keep the glyph
 * out of the DOM textContent traversal. This avoids double-rendering icons
 * in callouts and page titles.
 * NOTE(slim/html-export-pseudo-icons): I can't tagref this because it will
 * flag as a duplicate tag after codegen.
 */
.icon[data-emoji]::before {
	content: attr(data-emoji);
}

img.icon {
	border-radius: 3px;
}

.callout img.notion-static-icon {
	width: 1em;
	height: 1em;
}

.callout p {
	margin: 0;
}

.callout h1,
.callout h2,
.callout h3 {
	margin: 0 0 0.6rem;
}

.user-icon {
	width: 1.5em;
	height: 1.5em;
	border-radius: 100%;
	margin-right: 0.5rem;
}

.user-icon-inner {
	font-size: 0.8em;
}

.text-icon {
	border: 1px solid #000;
	text-align: center;
}

.page-cover-image {
	display: block;
	object-fit: cover;
	width: 100%;
	max-height: 30vh;
}

.page-header-icon {
	font-size: 3rem;
	margin-bottom: 1rem;
}

.page-header-icon-with-cover {
	margin-top: -0.72em;
	margin-left: 0.07em;
}

.page-header-icon img {
	border-radius: 3px;
}

.link-to-page {
	margin: 1em 0;
	padding: 0;
	border: none;
	font-weight: 500;
}

p > .user {
	opacity: 0.5;
}

td > .user,
td > time {
	white-space: nowrap;
}

input[type="checkbox"] {
	margin-right: 0.4em;
	vertical-align: middle;
}

p {
	margin-top: 0.5em;
	margin-bottom: 0.5em;
}

.image {
	border: none;
	margin: 1.5em 0;
	padding: 0;
	border-radius: 0;
	text-align: center;
}

.code,
code {
	background: rgba(135, 131, 120, 0.15);
	border-radius: 3px;
	padding: 0.2em 0.4em;
	border-radius: 3px;
	font-size: 85%;
	tab-size: 2;
}

code {
	color: #eb5757;
}

.code {
	padding: 1.5em 1em;
}

.code-wrap {
	white-space: pre-wrap;
	word-break: break-all;
}

.code > code {
	background: none;
	padding: 0;
	font-size: 100%;
	color: inherit;
}

blockquote {
	font-size: 1em;
	margin: 1em 0;
	padding-left: 1em;
	border-left: 3px solid rgb(55, 53, 47);
}

blockquote.quote-large {
	font-size: 1.25em;
}

.bookmark {
	text-decoration: none;
	max-height: 8em;
	padding: 0;
	display: flex;
	width: 100%;
	align-items: stretch;
}

.bookmark-title {
	font-size: 0.85em;
	overflow: hidden;
	text-overflow: ellipsis;
	height: 1.75em;
	white-space: nowrap;
}

.bookmark-text {
	display: flex;
	flex-direction: column;
}

.bookmark-info {
	flex: 4 1 180px;
	padding: 12px 14px 14px;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}

.bookmark-image {
	width: 33%;
	flex: 1 1 180px;
	display: block;
	position: relative;
	object-fit: cover;
	border-radius: 1px;
}

.bookmark-description {
	color: rgba(55, 53, 47, 0.6);
	font-size: 0.75em;
	overflow: hidden;
	max-height: 4.5em;
	word-break: break-word;
}

.bookmark-href {
	font-size: 0.75em;
	margin-top: 0.25em;
}

.tab {
	margin: 1.25em 0;
	padding-inline: 1rem;
	border: 1px solid rgba(55, 53, 47, 0.09);
}

.sans { font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", "Noto Sans Arabic", "Noto Sans Hebrew", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol"; }
.code { font-family: "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace; }
.serif { font-family: Lyon-Text, Georgia, ui-serif, serif; }
.mono { font-family: iawriter-mono, Nitti, Menlo, Courier, monospace; }
.pdf .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", "Noto Sans Arabic", "Noto Sans Hebrew", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK JP'; }
.pdf:lang(zh-CN) .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", "Noto Sans Arabic", "Noto Sans Hebrew", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK SC'; }
.pdf:lang(zh-TW) .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", "Noto Sans Arabic", "Noto Sans Hebrew", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK TC'; }
.pdf:lang(ko-KR) .sans { font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI Variable Display", "Segoe UI", Helvetica, "Apple Color Emoji", "Noto Sans Arabic", "Noto Sans Hebrew", Arial, sans-serif, "Segoe UI Emoji", "Segoe UI Symbol", 'Twemoji', 'Noto Color Emoji', 'Noto Sans CJK KR'; }
.pdf .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK JP'; }
.pdf:lang(zh-CN) .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK SC'; }
.pdf:lang(zh-TW) .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK TC'; }
.pdf:lang(ko-KR) .code { font-family: Source Code Pro, "SFMono-Regular", Menlo, Consolas, "PT Mono", "Liberation Mono", Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK KR'; }
.pdf .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK JP'; }
.pdf:lang(zh-CN) .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK SC'; }
.pdf:lang(zh-TW) .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK TC'; }
.pdf:lang(ko-KR) .serif { font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK KR'; }
.pdf .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK JP'; }
.pdf:lang(zh-CN) .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK SC'; }
.pdf:lang(zh-TW) .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK TC'; }
.pdf:lang(ko-KR) .mono { font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK KR'; }
.highlight-default {
	color: rgba(44, 44, 43, 1);
}
.highlight-gray {
	color: rgba(125, 122, 117, 1);
	fill: rgba(125, 122, 117, 1);
}
.highlight-brown {
	color: rgba(159, 118, 90, 1);
	fill: rgba(159, 118, 90, 1);
}
.highlight-orange {
	color: rgba(210, 123, 45, 1);
	fill: rgba(210, 123, 45, 1);
}
.highlight-yellow {
	color: rgba(203, 148, 52, 1);
	fill: rgba(203, 148, 52, 1);
}
.highlight-teal {
	color: rgba(80, 148, 110, 1);
	fill: rgba(80, 148, 110, 1);
}
.highlight-blue {
	color: rgba(56, 125, 201, 1);
	fill: rgba(56, 125, 201, 1);
}
.highlight-purple {
	color: rgba(154, 107, 180, 1);
	fill: rgba(154, 107, 180, 1);
}
.highlight-pink {
	color: rgba(193, 76, 138, 1);
	fill: rgba(193, 76, 138, 1);
}
.highlight-red {
	color: rgba(207, 81, 72, 1);
	fill: rgba(207, 81, 72, 1);
}
.highlight-default_background {
	color: rgba(44, 44, 43, 1);
}
.highlight-gray_background {
	background: rgba(42, 28, 0, 0.07);
}
.highlight-brown_background {
	background: rgba(139, 46, 0, 0.086);
}
.highlight-orange_background {
	background: rgba(224, 101, 1, 0.129);
}
.highlight-yellow_background {
	background: rgba(211, 168, 0, 0.137);
}
.highlight-teal_background {
	background: rgba(0, 100, 45, 0.09);
}
.highlight-blue_background {
	background: rgba(0, 124, 215, 0.094);
}
.highlight-purple_background {
	background: rgba(102, 0, 178, 0.078);
}
.highlight-pink_background {
	background: rgba(197, 0, 93, 0.086);
}
.highlight-red_background {
	background: rgba(223, 22, 0, 0.094);
}
.block-color-default {
	color: inherit;
	fill: inherit;
}
.block-color-gray {
	color: rgba(125, 122, 117, 1);
	fill: rgba(125, 122, 117, 1);
}
.block-color-brown {
	color: rgba(159, 118, 90, 1);
	fill: rgba(159, 118, 90, 1);
}
.block-color-orange {
	color: rgba(210, 123, 45, 1);
	fill: rgba(210, 123, 45, 1);
}
.block-color-yellow {
	color: rgba(203, 148, 52, 1);
	fill: rgba(203, 148, 52, 1);
}
.block-color-teal {
	color: rgba(80, 148, 110, 1);
	fill: rgba(80, 148, 110, 1);
}
.block-color-blue {
	color: rgba(56, 125, 201, 1);
	fill: rgba(56, 125, 201, 1);
}
.block-color-purple {
	color: rgba(154, 107, 180, 1);
	fill: rgba(154, 107, 180, 1);
}
.block-color-pink {
	color: rgba(193, 76, 138, 1);
	fill: rgba(193, 76, 138, 1);
}
.block-color-red {
	color: rgba(207, 81, 72, 1);
	fill: rgba(207, 81, 72, 1);
}
.block-color-default_background {
	color: inherit;
	fill: inherit;
}
.block-color-gray_background {
	background: rgba(240, 239, 237, 1);
}
.block-color-brown_background {
	background: rgba(245, 237, 233, 1);
}
.block-color-orange_background {
	background: rgba(251, 235, 222, 1);
}
.block-color-yellow_background {
	background: rgba(249, 243, 220, 1);
}
.block-color-teal_background {
	background: rgba(232, 241, 236, 1);
}
.block-color-blue_background {
	background: rgba(229, 242, 252, 1);
}
.block-color-purple_background {
	background: rgba(243, 235, 249, 1);
}
.block-color-pink_background {
	background: rgba(250, 233, 241, 1);
}
.block-color-red_background {
	background: rgba(252, 233, 231, 1);
}
.select-value-color-default { background-color: rgba(42, 28, 0, 0.07); }
.select-value-color-gray { background-color: rgba(28, 19, 1, 0.11); }
.select-value-color-brown { background-color: rgba(127, 51, 0, 0.156); }
.select-value-color-orange { background-color: rgba(196, 88, 0, 0.203); }
.select-value-color-yellow { background-color: rgba(209, 156, 0, 0.282); }
.select-value-color-green { background-color: rgba(0, 96, 38, 0.156); }
.select-value-color-blue { background-color: rgba(0, 118, 217, 0.203); }
.select-value-color-purple { background-color: rgba(92, 0, 163, 0.141); }
.select-value-color-pink { background-color: rgba(183, 0, 78, 0.152); }
.select-value-color-red { background-color: rgba(206, 24, 0, 0.164); }

.checkbox {
	display: inline-flex;
	vertical-align: text-bottom;
	width: 16;
	height: 16;
	background-size: 16px;
	margin-left: 2px;
	margin-right: 5px;
}

.checkbox-on {
	background-image: url("data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%0A%3Crect%20width%3D%2216%22%20height%3D%2216%22%20fill%3D%22%2358A9D7%22%2F%3E%0A%3Cpath%20d%3D%22M6.71429%2012.2852L14%204.9995L12.7143%203.71436L6.71429%209.71378L3.28571%206.2831L2%207.57092L6.71429%2012.2852Z%22%20fill%3D%22white%22%2F%3E%0A%3C%2Fsvg%3E");
}

.checkbox-off {
	background-image: url("data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%0A%3Crect%20x%3D%220.75%22%20y%3D%220.75%22%20width%3D%2214.5%22%20height%3D%2214.5%22%20fill%3D%22white%22%20stroke%3D%22%2336352F%22%20stroke-width%3D%221.5%22%2F%3E%0A%3C%2Fsvg%3E");
}
	
</style><style>@import url('https://cdn.jsdelivr.net/npm/katex@0.16.25/dist/katex-swap.min.css')</style></head><body><article id="0d4ce4f4-d108-8370-ac79-81740b2a82c1" class="page sans"><header><h1 class="page-title" dir="auto">포트폴리오</h1><p class="page-description" dir="auto"></p></header><div class="page-body"><h2 id="3c4ce4f4-d108-80b2-9e2c-dc4974537a4d" class="" dir="auto">합격뿌수기 | 2024.01. ~ 2026.07. (개인프로젝트)</h2><ul id="3c4ce4f4-d108-80a3-b753-e66b48f5c9e8" class="bulleted-list" dir="auto"><li style="list-style-type:disc">개요: 실시간 동영상 강의 스트리밍 서비스와 질문/소통 게시판 플랫폼</li></ul><ul id="3c4ce4f4-d108-8028-80c6-ef80eeadcf36" class="bulleted-list" dir="auto"><li style="list-style-type:disc">기술 스택<ul id="3c4ce4f4-d108-802b-bac6-ca6f0625d65a" class="bulleted-list" dir="auto"><li style="list-style-type:circle">Backend: Django, Node.js</li></ul><ul id="3c4ce4f4-d108-8090-9898-e286847d601b" class="bulleted-list" dir="auto"><li style="list-style-type:circle">Infra &amp; DevOps:  GCP Compute Engine, Linux, Nginx, Gunicorn, Certbot(TLS), CloudFlare(Reverse Proxy)</li></ul><ul id="3c4ce4f4-d108-8042-9b18-c4d1cdb9c13b" class="bulleted-list" dir="auto"><li style="list-style-type:circle">Database: Google Cloud SQL (MySQL 8.0)</li></ul></li></ul><ul id="3c4ce4f4-d108-8007-8860-ebbdacbd67bd" class="bulleted-list" dir="auto"><li style="list-style-type:disc">상세 업무<ul id="3c4ce4f4-d108-8016-98fe-e1501ca9982d" class="bulleted-list" dir="auto"><li style="list-style-type:circle">VPC Private IP를 이용한 네트워크 홉 레이턴시 개선과 직렬화 오버헤드 및 1+N 쿼리 문제 해결을 통한 Django ORM 최적화로 데이터 용량 45% 절감 및 API 응답 속도 97% 개선</li></ul><ul id="3c4ce4f4-d108-8026-95de-c37f965b3fb7" class="bulleted-list" dir="auto"><li style="list-style-type:circle">GCP, Nginx, Gunicorn, systemd 데몬 기반의 무중단 배포 환경구축 및 Certbot(TLS), CloudFlare(Reverse Proxy) 연동을 통한 HTTPS 보안 강화</li></ul><ul id="3c4ce4f4-d108-80fa-a635-c1684850a72d" class="bulleted-list" dir="auto"><li style="list-style-type:circle">Django 서버 토큰 기반 유저 인증/인가 시스템 구현 및 RESTful API 설계·개발</li></ul><ul id="3c4ce4f4-d108-8043-9608-cfb4ac57363b" class="bulleted-list" dir="auto"><li style="list-style-type:circle">Node.js 및 HLS 프로토콜 기반 동영상 스트리밍 서버 구축과 Toss Payments PG 결제 모듈 연동</li></ul></li></ul><p id="3c4ce4f4-d108-8007-a5f2-fa0662f31b49" class="" dir="auto">
</p><h4 id="3c4ce4f4-d108-80ed-874e-c3ac54be5eda" class="" dir="auto">기술설명</h4><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="📣" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-804a-afc0-f96ee93d1911" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="📣"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-8048-b4b6-d58cbfecf96b" class="" dir="auto">구현 기술에 대한 주된 메커니즘들을 설명합니다</p><p id="3c4ce4f4-d108-80e9-97f7-fb4fa7fefe2f" class="" dir="auto"> </p><p id="3c4ce4f4-d108-80be-aab8-f0a3944dfcfc" class="" dir="auto"> </p><p id="3c4ce4f4-d108-8009-90ff-f81a6560c98b" class="" dir="auto"> </p><p id="3c4ce4f4-d108-8021-8ec0-d6f715d42c90" class="" dir="auto"> </p><p id="3c4ce4f4-d108-8077-86e0-ec1db6044a01" class="" dir="auto"> </p></div></aside><h4 id="3c4ce4f4-d108-8038-b7cd-e2db19e5dad8" class="" dir="auto">1. 백엔드 아키텍처 및 성능 최적화</h4><p id="3c4ce4f4-d108-809f-9454-f7285490c256" class="" dir="auto">1) API 설계 및 DB 쿼리 최적화(select_related, annotate)</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-8058-b0fd-c965354c30e8" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-80a6-a90f-d8fb90dd3c2c" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-8087-81e6-e79808b3fed5" class="bulleted-list" dir="auto"><li style="list-style-type:disc">API 요청에 따른 지연시간 최소화와 데이터 안정성을 목표로 백엔드 서버 전반의 RESTful API를 설계</li></ul><p id="3c4ce4f4-d108-8063-9964-d671c0067a73" class="" dir="auto">문제 상황 </p><ul id="3c4ce4f4-d108-804b-a31f-dad7bbc8d7da" class="bulleted-list" dir="auto"><li style="list-style-type:disc">특정 조회 API 호출 시 314KB 데이터 반환에 3초가 소요되는 병목 발생</li></ul><p id="3c4ce4f4-d108-80e8-84d5-efcb1539f796" class="" dir="auto"><strong>가설 검증 </strong></p><ul id="3c4ce4f4-d108-8058-b218-e7eb596595e2" class="bulleted-list" dir="auto"><li style="list-style-type:disc">GCE - Cloud SQL 간 네트워크 홉 레이턴시를 의심하여 Public IP → VPC Private IP 환경으로 전환했으나 개선 미비. (인프라 이슈 배제)</li></ul><ul id="3c4ce4f4-d108-8015-9817-e404989cf79b" class="bulleted-list" dir="auto"><li style="list-style-type:disc">API 직렬화(Serialization) 과정에서의 오버헤드 및 1+N 쿼리 문제를 의심하고, 무분별하게 연결된 외래키 필드 제거 및 ORM 최적화(<code>select_related</code>, <code>annotate</code> 활용)를 통해 DB 레벨에서 최적화된 데이터만 추출하도록 수정</li></ul><script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/prism.min.js" integrity="sha512-7Z9J3l1+EYfeaPKcGXu3MS/7T+w19WtKQY/n+xzmw4hZhJ9tyYmcUS+4QqAlzhicE5LAfMQSF3iFTK9bQdTxXg==" crossorigin="anonymous" referrerPolicy="no-referrer"></script><link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism.min.css" integrity="sha512-tN7Ec6zAFaVSG3TpNAKtk4DOHNpSwKHxxrsiw4GHKESGPs5njn/0sMCUMl2svV4wo4BK/rCP7juYz+zx+l6oeQ==" crossorigin="anonymous" referrerPolicy="no-referrer"/><script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-python.min.js" integrity="sha512-AKaNmg8COK0zEbjTdMHJAPJ0z6VeNqvRvH4/d5M4sHJbQQUToMBtodq4HaV4fa+WV2UTfoperElm66c9/8cKmQ==" crossorigin="anonymous" referrerPolicy="no-referrer"></script><pre id="3c4ce4f4-d108-80d9-840b-ed71826195b8" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all"># select_related를 이용해 관련된 정보도 같이 가져옴으로써, 1+N 쿼리 문제를 해결
orders = Order.objects.select_related(&#x27;product&#x27;).annotate(
		# annotate를 이용해 배송 정보 존재 유무만 직렬화
    has_shipping=Exists(
        Shipping.objects.filter(order=OuterRef(&#x27;pk&#x27;))
    )
)</code></pre><figure id="3c4ce4f4-d108-8010-9b1f-e38cc983d708" class="image" data-notion-image="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image.png" dir="ltr"><a href="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image.png"><img style="width:637.953125px" src="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image.png"/></a></figure><p id="3c4ce4f4-d108-803a-9547-d72c3dc32ca7" class="" dir="auto">결과 </p><ul id="3c4ce4f4-d108-8031-8087-fa4d7c0295df" class="bulleted-list" dir="auto"><li style="list-style-type:disc">데이터 용량 <strong>45% 절감</strong> (314KB → 172KB), API 응답 속도 <strong>97% 개선</strong> (3.0초 → 0.09초). DB-Application 간의 효율적인 데이터 흐름 설계 능력을 배양함.</li></ul><p id="3c4ce4f4-d108-8044-a1bb-f76530a8c2c2" class="" dir="auto">
</p></div></aside><p id="3c4ce4f4-d108-8013-873f-ecf4c1f37e5f" class="" dir="auto">2) API 설계 및 DB 쿼리 최적화(F 객체)</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-80a9-a065-c7db423ebfc1" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-807d-92e9-ca7328b66a00" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-8074-b770-feb758e19463" class="bulleted-list" dir="auto"><li style="list-style-type:disc">재고 차감 및 수량 변경 시 발생하는 <strong>동시성 문제(Race Condition / Lost Update) 방지</strong> 및 불필요한 Read-Before-Write 쿼리 최소화</li></ul><p id="3c4ce4f4-d108-8002-98ae-fb315f4dd819" class="" dir="auto">기대 효과</p><ul id="3c4ce4f4-d108-80b5-8180-c07bca749556" class="bulleted-list" dir="auto"><li style="list-style-type:disc">메모리 로드 없이 DB 엔진 레벨에서 직접 연산을 수행하여  race condition 완벽 방지</li></ul><p id="3c4ce4f4-d108-80fc-b2b7-ea971699444f" class="" dir="auto">코드</p><pre id="3c4ce4f4-d108-808e-bf5f-d600647aa6fa" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all">Product.objects.filter(id=product_id).update(
    stock_quantity=F(&#x27;stock_quantity&#x27;) - 1
)</code></pre></div></aside><p id="3c4ce4f4-d108-80bd-9351-d2c2f2bc37ed" class="" dir="auto">
</p><h4 id="3c4ce4f4-d108-806e-9421-cb8ae37fc0cd" class="" dir="auto">2. 데이터베이스 설계 및 인덱싱 최적화</h4><p id="3c4ce4f4-d108-807c-9057-f3a116807a95" class="" dir="auto">1) DB 설계</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-8001-8827-d9f9fba6205c" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-8030-8740-f5e1eebdc188" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-8052-8ed5-d9039bb6010a" class="bulleted-list" dir="auto"><li style="list-style-type:disc">정규화를 통해 데이터 중복을 최소화하고, 엔티티 간 무결성과 독립성을 확보한 데이터베이스 아키텍처 구축</li></ul><p id="3c4ce4f4-d108-80a2-b7ca-c04f917f3f1f" class="" dir="auto">설계 방법</p><ul id="3c4ce4f4-d108-8037-8172-ff5b38ff135b" class="bulleted-list" dir="auto"><li style="list-style-type:disc"><code><strong>User</strong></code><strong> - </strong><code><strong>Product</strong></code><strong> (N:M 해소 및 데이터 스냅샷 보장)<br/><br/></strong><code>User</code>와 <code>Product</code> 간 다대다(N:M) 관계를 교차 테이블인 <code>Order</code>로 해소하고, 구매 시점의 가격(<code>final_price</code>)을 별도 보관하여 원본 상품 정보 변경에도 과거 결제 데이터의 무결성을 유지<br/></li></ul><ul id="3c4ce4f4-d108-801f-82f0-ea73f8cf20a8" class="bulleted-list" dir="auto"><li style="list-style-type:disc"><code>Order</code> - <code>Payment</code><strong> </strong>(1:1 역할 분리 및 관심사 분리)<br/><br/>주문 본체 데이터와 PG 결제 데이터(<code>Payment</code>)를 <code>1:1 (OneToOneField)</code> 관계로 분리 설계하여, 결제 시도·실패·취소 등의 상태 변화 라이프사이클이 주문 본문 데이터를 오염시키지 않도록 관심사를 명확히 격리<br/></li></ul><ul id="3c4ce4f4-d108-8056-8814-d71095e5f974" class="bulleted-list" dir="auto"><li style="list-style-type:disc"><code><strong>Order</strong></code><strong> - </strong><code><strong>Shipipng</strong></code> (최소 권한 기반의 데이터 보안 및 조회 최적화)<br/><br/>배송 발주 시스템에서 최소한의 데이터 테이블을 검색하고, 거래처 계정에 <code>Shipping</code> 테이블 조회 권한만 제공함으로써 데이터 패킷 최적화와 데이터베이스 보안을 향상</li></ul><p id="3c4ce4f4-d108-8021-9a4c-e5313cd3cf64" class="" dir="auto">결과(일부 필드 생략) </p><figure id="3c4ce4f4-d108-80d0-8606-cc56fd2574f3" class="image" data-notion-image="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%201.png" dir="ltr"><a href="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%201.png"><img style="width:637.96875px" src="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%201.png"/></a></figure></div></aside><p id="3c4ce4f4-d108-8030-9da1-c07a099e248c" class="" dir="auto">2) DB 인덱싱 최적화</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-801e-b4f4-eae427aa5053" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-802c-a045-cf9368c9a713" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-802c-b253-fe3024a41eec" class="bulleted-list" dir="auto"><li style="list-style-type:disc">빈번하게 발생하는 필터링·정렬 조건에 최적화된 인덱스를 구성하여, DB CPU 사용량 절감 및 쿼리 응답 속도 최적화</li></ul><p id="3c4ce4f4-d108-80a7-a348-ec950b352370" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-807b-9af8-da9d189d7c7b" class="bulleted-list" dir="auto"><li style="list-style-type:disc"><code>User.email</code>,<code>Payment.payments_key</code> (<code>Unique Index</code>)<ul id="3c4ce4f4-d108-80f3-ac36-e335590a0a54" class="bulleted-list" dir="auto"><li style="list-style-type:circle"><strong>설계 이유:</strong> 고유 식별자 단건 조회 시  테이블 전체 검색을 방지하고 데이터 중복을 근본적으로 차단하기 위해 설정</li></ul><ul id="3c4ce4f4-d108-8015-9bda-c43e5d4d0962" class="bulleted-list" dir="auto"><li style="list-style-type:circle"><strong>기대 효과:</strong> O(1) 수준의 조회 속도 확보 및 데이터 유일성(Uniqueness) 제약 강제</li></ul><pre id="3c4ce4f4-d108-804f-b5ff-e775ad2fc8c3" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all">class User(AbstractBaseUser, PermissionsMixin):
		# 이메일 필드(필수, 검색)
    email = models.EmailField(
		    unique=True
    )
    
class Payment(models.Model):
    # 결제 키 필드(검색, 결제취소)
    payments_key = models.CharField(
        max_length=200,
        unique=True
    )</code></pre></li></ul><p id="3c4ce4f4-d108-8041-affb-ffce2547fe79" class="" dir="auto">
</p><ul id="3c4ce4f4-d108-80ed-97ce-ed128ce626a0" class="bulleted-list" dir="auto"><li style="list-style-type:disc"><code><strong>Order.purchase_date</strong></code><strong> (</strong><code><strong>db_index=True</strong></code><strong> 단일 인덱스)</strong><ul id="3c4ce4f4-d108-8027-82ea-cb3eb346e56d" class="bulleted-list" dir="auto"><li style="list-style-type:circle"><strong>설계 이유:</strong> 특정 기간의 주문 내역 조회 및 최신순 정렬(<code>ORDER BY purchase_date DESC</code>) 쿼리가 빈번하게 발생하는 점을 고려하여 설정.</li></ul><ul id="3c4ce4f4-d108-80f1-933d-c793a67d5c26" class="bulleted-list" dir="auto"><li style="list-style-type:circle"><strong>기대 효과:</strong> DB의 추가적인 메모리/CPU 정렬 연산을 제거하고, 기간 검색 범위를 최소화하여 읽기 성능 향상.</li></ul><pre id="3c4ce4f4-d108-80ee-8a94-efeeaae679c6" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all">class Order(models.Model):
    purchase_date = models.DateTimeField(
        auto_now_add=True, 
        db_index=True
    )</code></pre></li></ul><p id="3c4ce4f4-d108-80cb-a418-da1731109b02" class="" dir="auto">
</p><ul id="3c4ce4f4-d108-80fe-885b-da2eba794b7a" class="bulleted-list" dir="auto"><li style="list-style-type:disc"><code><strong>Payment.payment_state</strong></code><strong> + </strong><code><strong>Payment.created_at</strong></code><strong> (</strong><code><strong>Composite Index</strong></code><strong> 복합 인덱스)</strong><ul id="3c4ce4f4-d108-80e0-842e-f711337682d8" class="bulleted-list" dir="auto"><li style="list-style-type:circle"><strong>설계 이유:</strong> &quot;특정 상태(예: 결제 대기)인 데이터 중 특정 기간 내 작성된 건&quot;을 필터링하는 조건 검색 패턴에 최적화하기 위해 설정</li></ul><ul id="3c4ce4f4-d108-80d2-9ffd-c32c1f6e1b62" class="bulleted-list" dir="auto"><li style="list-style-type:circle"><strong>기대 효과:</strong> 단일 필드 인덱싱 시 발생하는 불필요한 레코드 스캔을 최소화하고, 결제 정산 및 상태 추적 배치(Batch) 쿼리 속도 극대화</li></ul><pre id="3c4ce4f4-d108-80c1-a010-e1bcfa3f2fdc" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all">class Payment(models.Model):
    STATE_CHOICES = [
        (&#x27;SUCCESS&#x27;, &#x27;결제 완료&#x27;),
        (&#x27;WAITING_CANCEL&#x27;, &#x27;취소 대기&#x27;),
        (&#x27;CANCELED&#x27;, &#x27;취소 완료&#x27;),
    ]
    
    # 결제 상태 (결제 완료, 취소 대기, 취소 완료)
    payment_state = models.CharField(max_length=20, choices=STATE_CHOICES, default=&#x27;SUCCESS&#x27;)
    # 거래 일시
    created_at = models.DateTimeField(auto_now_add=True)

    class Meta:
        indexes = [
            # [복합 인덱스] 결제 상태별/기간별 내역 조회 최적화 (어드민 / 유저 결제 조회)
            models.Index(fields=[&#x27;payment_state&#x27;, &#x27;created_at&#x27;], name=&#x27;idx_pay_state_created&#x27;),
        ]</code></pre></li></ul></div></aside><p id="3c4ce4f4-d108-80a1-9697-f4fcd84737ba" class="" dir="auto">
</p><h4 id="3c4ce4f4-d108-80fe-8491-df905cf2dca9" class="" dir="auto">3. 인프라 및 네트워크 설계 </h4><figure id="3c4ce4f4-d108-8092-a2cf-f875a246d0d9" class="image" data-notion-image="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%202.png" dir="ltr"><a href="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%202.png"><img style="width:577.984375px" src="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%202.png"/></a></figure><p id="3c4ce4f4-d108-8012-a6d3-fea69ad07287" class="" dir="auto">1) GCP 기반의 클라우드 인프라 구축</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-80f8-a896-e47dfe32c3eb" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-805f-92ca-c76baf5ec73d" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-80c3-8c39-c0b8329c5104" class="bulleted-list" dir="auto"><li style="list-style-type:disc">GCP 생태계를 활용하여 컴퓨팅, DB, 스토리지를 분리함으로써 서비스의 가용성 확보하고 안정적인 서버 운영 환경 구축</li></ul><p id="3c4ce4f4-d108-8098-b01e-e8ce326a265b" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-802b-a316-cfab7466c8a5" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Compute Engine: Linux OS 기반 서버 구축 및 외부 고정 IP(Static IP) 할당을 통한 안정적인 서버 엔드포인트 운용<br/></li></ul><ul id="3c4ce4f4-d108-80af-a0f5-e1da80385c4b" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Cloud SQL: MySQL 8.0 기반으로 애플리케이션 서버와 DB를 분리하고, VPC 내부 IP 연동을 통해 외부 무단 접근 차단 및 네트워크 홉(Hop) 감소로 데이터 통신 성능과 비용 최적화<br/></li></ul><ul id="3c4ce4f4-d108-803c-9396-d0feb697c9f8" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Cloud Storage: 정적 자원 및 유저 미디어 파일을 GCS 버킷으로 격리하여 서버 I/O 부담을 해소하고, 프라이빗 버킷에서 서명된 URL(Signed URL) 방식을 적용해 파일 보안 및 권한 검증 처리를 GCP 서비스로 이관</li></ul></div></aside><p id="3c4ce4f4-d108-80c7-b926-e2e699ecbdab" class="" dir="auto">2) 웹 서버 및 네트워크 아키텍처 최적화</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-800d-8fab-c6e296e21b17" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-80a8-91a3-c9f6e86e4ea6" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-80c7-9665-d0c66ff39793" class="bulleted-list" dir="auto"><li style="list-style-type:disc">클라이언트와 애플리케이션 간 보안성 강화 및 WSGI/Reverse Proxy 레이어 구성을 통한 웹 요청 처리 성능 최적화</li></ul><p id="3c4ce4f4-d108-80ed-aecb-ef268437eb25" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-8082-939c-e26d0e5184a8" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Nginx &amp; Gunicorn: Nginx를 Reverse Proxy로 두어 정적 파일 처리 및 SSL 종단을 담당하게 하고, Unix Socket 연동 기반의 Gunicorn(WSGI)을 통해 Django 애플리케이션으로의 요청 동시성 효율화<br/></li></ul><ul id="3c4ce4f4-d108-801b-843f-e2c787c2d266" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Cloud Flare: DNS 타깃팅 및 Reverse Proxy모드를 적용하여 원천 서버 IP 노출을 차단하고 DDoS 등 외부 보안 위협 1차 방어</li></ul></div></aside><p id="3c4ce4f4-d108-8012-b6f2-dbe653af0067" class="" dir="auto">
</p><h4 id="3c4ce4f4-d108-8013-93b3-ea1a33e962df" class="" dir="auto">4. 시스템 및 인증 보안</h4><p id="3c4ce4f4-d108-80fe-ae6a-d3cca2f2d542" class="" dir="auto">1) Cloud SQL 데이터베이스 보안 및 감사 체계 구축</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-8097-8c80-fac1335ee969" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-80ad-a59f-f992b9674cd9" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-8052-be79-da98c5c6f388" class="bulleted-list" dir="auto"><li style="list-style-type:disc">데이터베이스 레이어의 네트워크 격리, 전송 구간 암호화, 최소 권한 적용 및 감사 로그 체계를 구축하여 외부 데이터 침해 방지 및 시스템 추적성 강화</li></ul><p id="3c4ce4f4-d108-802f-a519-d60f97ebfe27" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-8088-b046-fc039eefb70d" class="bulleted-list" dir="auto"><li style="list-style-type:disc">비공개 IP 전용 구성: Cloud SQL을 VPC 내부 전용 IP로 전환하여 공용 인터넷 노출을 차단<br/></li></ul><ul id="3c4ce4f4-d108-80ab-bd07-c7c40be9dcd3" class="bulleted-list" dir="auto"><li style="list-style-type:disc">전송 구간 SSL/TLS 암호화 및 패킷 검증: <code>&#x27;ssl_mode&#x27;: &#x27;REQUIRED&#x27;</code> 옵션 적용</li></ul><pre id="3c4ce4f4-d108-80e8-bc75-c29ee80087a5" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all">&#x27;OPTIONS&#x27;: {
      &#x27;charset&#x27;: &#x27;utf8mb4&#x27;,
      &#x27;ssl&#x27;: {
          &#x27;ssl_mode&#x27;: &#x27;REQUIRED&#x27;    # 데이터 전송 암호화 강제!
      }
},</code></pre><script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-bash.min.js" integrity="sha512-whYhDwtTmlC/NpZlCr6PSsAaLOrfjVg/iXAnC4H/dtiHawpShhT2SlIMbpIhT/IL/NrpdMm+Hq2C13+VKpHTYw==" crossorigin="anonymous" referrerPolicy="no-referrer"></script><pre id="3c4ce4f4-d108-800b-bea0-c9a4ce1ebba0" class="code code-wrap" data-notion-code-syntax="bash"><code class="language-bash" style="white-space:pre-wrap;word-break:break-all">sudo tcpdump -i any -X -vv port 3306

# 암호화 전
0x0240:  5f70 6466 1864 6f77 6e6c 6f61 645f 6578  _pdf.download_ex

# 암호화 후
0x0240:  b032 6a20 e1a7 d2b2 2431 e14f 2db3 e01b  .2j.....$1.O-...</code></pre><p id="3c4ce4f4-d108-80e3-afc1-f49c1fe780c5" class="" dir="auto">
</p><ul id="3c4ce4f4-d108-80a2-9426-d39422f4902a" class="bulleted-list" dir="auto"><li style="list-style-type:disc">최소 권한 원칙(Principle of Least Privilege) 계정 관리: 기존 <code>root</code> 접속 방식에서 탈피하여 서비스 전용 최소 권한 계정(<code>django_user</code>)으로 DB 인가 권한 제한<br/></li></ul><ul id="3c4ce4f4-d108-80e3-9102-cfc34d8fd92b" class="bulleted-list" dir="auto"><li style="list-style-type:disc">GCP Cloud Audit Logging 감사 체계 구축: DB 감사 플래그(<code>cloudsql_mysql_audit = ON</code>) 및 IAM 연동을 설정하고 Log Explorer 쿼리를 활용한 DML 추적 환경 구성<figure id="3c4ce4f4-d108-8094-b1f9-ca51394dbc15" class="image" style="text-align:left" data-notion-image="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%203.png" dir="ltr"><a href="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%203.png"><img style="width:516.96875px" src="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%203.png"/></a></figure><p id="3c4ce4f4-d108-8006-98bb-c569913fe942" class="" dir="auto">로그 탐색기에서 LQL 설정시 다음과 같은 내용을 확인할 수 있다 <br/>(현재 general_log를 통해서 검색)</p><figure id="3c4ce4f4-d108-8051-b4ec-f99d32fe744d" class="image" data-notion-image="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%204.png" dir="ltr"><a href="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%204.png"><img style="width:594.984375px" src="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%204.png"/></a></figure></li></ul></div></aside><p id="3c4ce4f4-d108-8004-a548-cd4a3d816a4e" class="" dir="auto">2) Django 기본 토큰 기반 유저 인증</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-8032-abde-df7107569b1c" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-801b-bd43-ea2af1a89e9e" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-805b-ba0e-e6cf5a688934" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Django 기본 TokenAuthentication 구조를 활용하여 API 요청별 사용자 접근 권한 검증 강화</li></ul><p id="3c4ce4f4-d108-808d-b74d-cbf282e0e584" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-80c1-9f40-f447530cfcda" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Django TokenAuthentication 적용: 유저 로그인 시 서버 단에서 고유 Token을 발급·매핑하고, HTTP Header를 통한 요청 검증 처리<br/></li></ul><ul id="3c4ce4f4-d108-80d1-918a-f654bf1b1b09" class="bulleted-list" dir="auto"><li style="list-style-type:disc">RESTful API 권한 제어: <code>@permission_classes([IsAuthenticated])</code>를 활용해 보호된 엔드포인트에 대한 무단 접근 차단<br/></li></ul><p id="3c4ce4f4-d108-80d2-b507-d69523edc453" class="" dir="auto">코드</p><pre id="3c4ce4f4-d108-807a-89ca-d5897262e7d9" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all"># 로그인 시, 토큰 생성 및 조회 후 Response로 돌려줌

token, _ = Token.objects.get_or_create(user=user)
        
return Response(
    {
        &#x27;user_id&#x27;: user.id, &#x27;token&#x27;: token.key 
    },
    status=status.HTTP_200_OK
)</code></pre><pre id="3c4ce4f4-d108-8000-a4ed-dc78f225c6a4" class="code code-wrap" data-notion-code-syntax="dart"><code class="language-dart" style="white-space:pre-wrap;word-break:break-all">// 웹에서 request 시, header에 토큰을 담아서 전송

final response = await http.get(
  Uri.https(ApiHelper.djangoServerApiAddr, &#x27;/user/getUser&#x27;),
  headers: {
    &#x27;Authorization&#x27;: &#x27;Token $token&#x27;, // 토큰 헤더로 전달
  },
);</code></pre><pre id="3c4ce4f4-d108-801b-b36d-d59ca60b90a6" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all"># 해더의 인증 토큰을 파싱하여 인증된 유저의 요청만 response하도록 데코레이터 설정

@api_view([&#x27;GET&#x27;])
@permission_classes([IsAuthenticated])
def get_user(request):
		# ..기타 예외 처리 생략.. 

    # 헤더의 토큰으로 검증된 request.user 객체를 직렬화함
    serializer = UserSerializer(request.user)
    
    return Response(
        serializer.data,
        status=status.HTTP_200_OK
    )</code></pre></div></aside><p id="3c4ce4f4-d108-80c7-89f8-e294e7c8ba99" class="" dir="auto">
</p><h4 id="3c4ce4f4-d108-808c-bd76-fa65929de08f" class="" dir="auto">5. HLS 기반 미디어 스트리밍 서버 분리 구축 및 토스페이먼츠 PG 연동</h4><p id="3c4ce4f4-d108-80f6-beb9-e4b1e01a82e3" class="" dir="auto">1) Cloud SQL 데이터베이스 보안 및 감사 체계 구축</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-80a1-8574-e96c37c90ca7" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-8012-b4f2-d0cb666229b6" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-8063-afbe-c0648f97f1bf" class="bulleted-list" dir="auto"><li style="list-style-type:disc">메인 웹 서버(Django)의 동영상 I/O 병목 현상을 방지하기 위해 비동기 처리 기반의 Node.js 스트리밍 전용 모듈 구축</li></ul><p id="3c4ce4f4-d108-80c4-b325-d4f3b6f7e7f4" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-805a-a304-dd367eb80f12" class="bulleted-list" dir="auto"><li style="list-style-type:disc">Nginx 리버스 프록시 연동: 서브도메인으로 유입되는 HTTP 트래픽을 내부 HLS_SERVER_PORT 포트의 Node.js 서버로 전달하여 보안성 및 TLS 처리 분리</li></ul><pre id="3c4ce4f4-d108-8009-b088-d581a0df7222" class="code code-wrap" data-notion-code-syntax="bash"><code class="language-bash" style="white-space:pre-wrap;word-break:break-all"># 2. Nginx 설정 
server {
    server_name SUB_DOMAIN;

    location / {
        proxy_pass http://127.0.0.1:HLS_SERVER_PORT;
    }
}</code></pre><p id="3c4ce4f4-d108-80b2-8519-eb88b2671681" class="" dir="auto">
</p><ul id="3c4ce4f4-d108-80f7-95e2-e5d56af0bdde" class="bulleted-list" dir="auto"><li style="list-style-type:disc">GCS 비공개 버킷 스트림 연동: 로컬 디스크 저장 방식 대신 <code>@google-cloud/storage</code> SDK를 통해 GCS 버킷 내 HLS 파일 존재 여부(<code>exists</code>)를 검증하고, 읽기 스트림(<code>createReadStream</code>)을 생성하여 서버 메모리 점유 최소화</li></ul><script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-jsx.min.js" integrity="sha512-m3JYEI6gx5fh9jF10FjGoMzVKcV2N6nchcDcqPCdI1L3R2WQV7br2XVNR8iTLb2daOMRl3zldbcfT40xU2ntVw==" crossorigin="anonymous" referrerPolicy="no-referrer"></script><pre id="3c4ce4f4-d108-808e-a364-d3af32ffb712" class="code code-wrap" data-notion-code-syntax="jsx"><code class="language-jsx" style="white-space:pre-wrap;word-break:break-all">// hls request 필터 및 파일 유무 확인
exists: async (req, cb) =&gt; {
    if (!req.url.endsWith(&#x27;.m3u8&#x27;) &amp;&amp; !req.url.endsWith(&#x27;.ts&#x27;)) { //.. 생략}
    else {
		    // .. 중략
		    const [exists] = await storage.bucket(bucketName).file(filePath).exists();

	      if (exists) {
	        return cb(null, true); // 파일 유무 확인 후 플래그 반환
	      }
    }
}</code></pre><pre id="3c4ce4f4-d108-808d-90a8-e68a7d75903f" class="code code-wrap" data-notion-code-syntax="jsx"><code class="language-jsx" style="white-space:pre-wrap;word-break:break-all">// .ts 파일 반환 과정
getSegmentStream: (req, cb) =&gt; {
  const filePath = req.url.substring(1); 
  const file = storage.bucket(bucketName).file(filePath); 
  const stream = file.createReadStream(); // 비동기 스트림 생성 (메모리 최적화)

  // .. 
  
  cb(null, stream);
}</code></pre></div></aside><p id="3c4ce4f4-d108-8004-9b44-cbf5be0114e3" class="" dir="auto">2) 토스페이먼츠 PG 연동</p><aside class="block-color-gray_background callout" data-notion-callout="" data-notion-callout-icon="🛠️" data-notion-callout-background="gray_background" style="white-space:pre-wrap;display:flex" id="3c4ce4f4-d108-80af-a16d-c9f69269a392" dir="ltr"><div style="font-size:1.5em"><span class="icon" data-emoji="🛠️"></span></div><div style="width:100%"><p id="3c4ce4f4-d108-80ca-81fa-f707b9dc5f69" class="" dir="auto">구현 목표</p><ul id="3c4ce4f4-d108-8046-95ee-e6fbbda1caa1" class="bulleted-list" dir="auto"><li style="list-style-type:disc">클라이언트-서버 간 금액 검증으로 결제 데이터 위변조를 차단하고, 실패 시나리오별 예외 처리를 통해 결제 트랜잭션의 무결성과 안정성을 확보</li></ul><p id="3c4ce4f4-d108-800c-b631-ec3b18ca35e1" class="" dir="auto">구현 내용</p><ul id="3c4ce4f4-d108-802d-9408-c06543c46779" class="bulleted-list" dir="auto"><li style="list-style-type:disc">6번: 토스페이먼츠 API 스펙에 따라 결제 요청과 최종 승인(Confirm) 과정을 분리하여 처리</li></ul><ul id="3c4ce4f4-d108-8076-ab27-e9df70ffb316" class="bulleted-list" dir="auto"><li style="list-style-type:disc">7번: 2번 과정에서 서버 DB에 저장한 주문 데이터(유저, 금액)와 6번에서 전달받은 결제 정보가 일치하는지 검증 (4번 클라이언트 단계에서의 금액 변조 차단)</li></ul><figure id="3c4ce4f4-d108-8058-959c-ce8752c68fec" class="image" style="text-align:center" data-notion-image="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%205.png" dir="ltr"><a href="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%205.png"><img style="width:528px" src="%ED%8F%AC%ED%8A%B8%ED%8F%B4%EB%A6%AC%EC%98%A4/image%205.png"/></a></figure><p id="3c4ce4f4-d108-800f-9115-d25deaa1c4fe" class="" dir="auto">코드</p><pre id="3c4ce4f4-d108-80e4-b46a-fe2373a2627b" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all"># get_payments_page 결제하기 버튼 클릭

@permission_classes([IsAuthenticated])
@xframe_options_exempt
def get_payments_page(request, orderID):
    try:
        context = {
						# 구매자 정보, 금액
        }
    # ..생략..

    return render(request, &#x27;payments.html&#x27;, context)</code></pre><pre id="3c4ce4f4-d108-8015-9e4c-f313d097f89e" class="code code-wrap" data-notion-code-syntax="jsx"><code class="language-jsx" style="white-space:pre-wrap;word-break:break-all">// payments.html에서 requestPayment()를 호출

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
            </code></pre><pre id="3c4ce4f4-d108-8082-8c7a-cf29b647fdb8" class="code code-wrap" data-notion-code-syntax="python"><code class="language-python" style="white-space:pre-wrap;word-break:break-all"># 유저의 결제 요청과 함게 결제 성공 여부를 tosspayments api를 통해 확인

# 결제 성공 여부를 확정 짓는 API
@api_view([&#x27;POST&#x27;])
def confirm(request) :
    try:
       # 결제 유저 검증
       # 결제 금액 검증
       
        conn = http.client.HTTPSConnection(&quot;api.tosspayments.com&quot;)
        # payload 생성
       
        headers = {
            &#x27;Authorization&#x27;: encrypted_secret_key,
            &#x27;Content-Type&#x27;: &quot;application/json&quot;
        }
        conn.request(&quot;POST&quot;, &quot;/v1/payments/confirm&quot;, payload_json, headers)

				
				# 이후 response 에서 결제 확인이 되면 
				# 결제 성공 비즈니스 로직을 실행</code></pre></div></aside></div></article><span class="sans" style="font-size:14px;padding-top:2em"></span></body></html>
