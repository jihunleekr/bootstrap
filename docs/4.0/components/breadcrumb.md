---
layout: docs
title: 경로
description: CSS 를 통해 자동으로 추가된 구분자로 탐색 계층 내에서 현재 페이지의 위치를 나타냅니다.
group: components
---

## 개요

구분자는 [`::before`](https://developer.mozilla.org/en-US/docs/Web/CSS/::before) 와 [`content`](https://developer.mozilla.org/en-US/docs/Web/CSS/content) 를 통해 CSS 에서 자동으로 추가됩니다.

{% capture example %}
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item active" aria-current="page">Home</li>
  </ol>
</nav>

<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>

<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item"><a href="#">Library</a></li>
    <li class="breadcrumb-item active" aria-current="page">Data</li>
  </ol>
</nav>
{% endcapture %}
{% include example.html content=example %}

## 접근성

경로는 탐색을 제공하기 때문에, `<nav>` 요소에 탐색 유형을 설명하기 위한 `aria-label="breadcrumb"` 같은 의미있는 레이블을 추가하는 것은 좋은 생각입니다. 또한, 현재 페이지를 나타내기 위해 마지막 항목에 `aria-current="page"` 를 적용하는 것도 좋습니다.

자세한 내용은, [WAI-ARIA Authoring Practices for the breadcrumb pattern](https://www.w3.org/TR/wai-aria-practices/#breadcrumb) 을 참고하세요.
