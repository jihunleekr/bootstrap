---
layout: docs
title: 개요
description: 감싸는 컨테이너, 강력한 그리드 시스템, 유연한 미디어 개체, 반응형 유틸리티 클래스를 포함한 부트스트랩 프로젝트의 레이아웃을 위한 컴포넌트와 옵션.
group: layout
redirect_from: "/docs/4.0/layout/"
toc: true
---

## 컨테이너

컨테이너는 부트스트랩에서 가장 기본적인 레이아웃 요소이며 **기본 그리드 시스템을 사용시 필수입니다**. 반응형, 고정폭 컨테이너 (각 중단점에서 `max-width` 변경을 의미), 유동폭 (항상 `100%` 너비라는 의미) 중에서 선택하세요.

컨테이너는 중첩될 수 있지만, 대부분의 레이아웃에는 중첩된 컨테이너가 필요하지 않습니다.

<div class="bd-example">
  <div class="bd-example-container">
    <div class="bd-example-container-header"></div>
    <div class="bd-example-container-sidebar"></div>
    <div class="bd-example-container-body"></div>
  </div>
</div>

{% highlight html %}
<div class="container">
  <!-- Content here -->
</div>
{% endhighlight %}

뷰포트 전체 너비에 맞춘 최대폭 컨테이너는 `.container-fluid` 를 사용하세요.

<div class="bd-example">
  <div class="bd-example-container bd-example-container-fluid">
    <div class="bd-example-container-header"></div>
    <div class="bd-example-container-sidebar"></div>
    <div class="bd-example-container-body"></div>
  </div>
</div>

{% highlight html %}
<div class="container-fluid">
  ...
</div>
{% endhighlight %}


## 반응형 중단점

부트스트랩은 모바일 우선으로 개발된 이후부터, 우리는 레이아웃과 인터페이스를 위해 적합한 중단점을 만들기 위해 약간의 [미디어 쿼리](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) 를 사용합니다. 이 중단점은 대부분 최소 뷰포트 너비를 기반으로 하며 뷰포트 변경시 요소의 크기를 조정할 수 있습니다.

부트스트랩은 레이아웃, 그리드 시스템, 컴포넌트에 대해 Sass 소스 파일의 다음과 같은 미디어 쿼리 범위(중단점)를 기본적으로 사용합니다.

{% highlight scss %}
// 초소형 장치 (휴대폰 세로방향, 576px 미만)
// 부트스트랩에서 기본값이므로 미디어 쿼리가 없습니다

// 소형 장치 (휴대폰 가로방향, 576px 이상)
@media (min-width: 576px) { ... }

// 중형 장치 (태블릿, 768px 이상)
@media (min-width: 768px) { ... }

// 대형 장치 (데스크탑, 992px 이상)
@media (min-width: 992px) { ... }

// 초대형 장치 (대형 데스크탑, 1200px 이상)
@media (min-width: 1200px) { ... }
{% endhighlight %}

Sass 에서 CSS 를 작성하고부터는, 모든 미디어 쿼리는 Sass 믹스인을 통해 사용가능합니다.

{% highlight scss %}
@include media-breakpoint-up(xs) { ... }
@include media-breakpoint-up(sm) { ... }
@include media-breakpoint-up(md) { ... }
@include media-breakpoint-up(lg) { ... }
@include media-breakpoint-up(xl) { ... }

// Example usage:
@include media-breakpoint-up(sm) {
  .some-class {
    display: block;
  }
}
{% endhighlight %}

우리는 가끔 미디어 쿼리를 다른 방향 (주어진 화면 크기 *이하*) 으로 사용하기도 합니다.

{% highlight scss %}
// 초소형 장치 (휴대폰 세로방향, 576px 미만)
@media (max-width: 575.98px) { ... }

// 소형 장치 (휴대폰 가로방향, 768px 미만)
@media (max-width: 767.98px) { ... }

// 중형 장치 (태블릿, 992px 미만)
@media (max-width: 991.98px) { ... }

// 대형 장치 (데스크탑, 1200px 미만)
@media (max-width: 1199.98px) { ... }

// 초대형 장치 (대형 데스크탑)
// 초대형 장치 중단점에는 너비 상한선이 없으므로 미디어 쿼리는 없습니다
{% endhighlight %}

{% include callout-info-mediaqueries-breakpoints.md %}

물론, 이 미디어 쿼리도 Sass 믹스인을 통해 사용이 가능합니다.

{% highlight scss %}
@include media-breakpoint-down(xs) { ... }
@include media-breakpoint-down(sm) { ... }
@include media-breakpoint-down(md) { ... }
@include media-breakpoint-down(lg) { ... }
{% endhighlight %}

또한 최소 및 최대 중단점 너비를 이용하여 특정 화면 크기를 대상으로 하는 미디어 쿼리 및 믹스인도 있습니다.

{% highlight scss %}
// 초소형 장치 (휴대폰 세로방향, 576px 미만)
@media (max-width: 575.98px) { ... }

// 소형 장치 (휴대폰 가로방향, 576px 이상)
@media (min-width: 576px) and (max-width: 767.98px) { ... }

// 중형 장치 (태블릿, 768px 이상)
@media (min-width: 768px) and (max-width: 991.98px) { ... }

// 대형 장치 (데스크탑, 992px 이상)
@media (min-width: 992px) and (max-width: 1199.98px) { ... }

// 초대형 장치 (대형 데스크탑, 1200px 이상)
@media (min-width: 1200px) { ... }
{% endhighlight %}

또한 이 미디어 쿼리도 Sass 믹스인을 통해 사용이 가능합니다.

{% highlight scss %}
@include media-breakpoint-only(xs) { ... }
@include media-breakpoint-only(sm) { ... }
@include media-breakpoint-only(md) { ... }
@include media-breakpoint-only(lg) { ... }
@include media-breakpoint-only(xl) { ... }
{% endhighlight %}

마찬가지로, 미디어 쿼리는 여러 중단점 너비에 걸쳐 있을 수도 있습니다.

{% highlight scss %}
// 예제
// 중형 장치부터 대형 장치까지 적용합니다.
@media (min-width: 768px) and (max-width: 1199.98px) { ... }
{% endhighlight %}

동일한 화면 크기 범위를 대상으로 하는 Sass 믹스인은 다음과 같습니다.

{% highlight scss %}
@include media-breakpoint-between(md, xl) { ... }
{% endhighlight %}

## Z-index

몇몇 부트스트랩 컴포넌트는 콘텐츠을 정렬하기 위한 세번째 축을 제공하여 레이아웃을 제어하는데 도움을 주는 CSS 속성인 `z-index` 를 사용합니다. 네비게이션, 툴팁, 팝오버, 모달 등을 적절하게 놓기 위해 설계된 부트스트랩의 기본 z-index 등급을 사용합니다. 

이러한 높은 값은 충돌을 이론적으로 피하기 충분한 임의의 수부터 시작하여 높게 지정됩니다. 우리는 동작에서 합리적으로 일관될 수 있도록 계층적 컴포넌트(툴팁, 팝오버, navbar, 드롭다운, 모달) 전반에 걸쳐 표준 세트가 필요합니다. 우리가 `100` 단위 또는 `500` 단위를 사용할 수 없었던 이유는 딱히 없습니다.

우리는 이러한 개별 값들을 맞춤화하는 것을 장려하지 않습니다. 만약 하나를 변경해야한다면, 모두를 바꿔야 할 것입니다.

{% highlight scss %}
$zindex-dropdown:          1000 !default;
$zindex-sticky:            1020 !default;
$zindex-fixed:             1030 !default;
$zindex-modal-backdrop:    1040 !default;
$zindex-modal:             1050 !default;
$zindex-popover:           1060 !default;
$zindex-tooltip:           1070 !default;
{% endhighlight %}

컴포넌트 (예: 입력그룹의 버튼과 입력) 에서 테두리가 겹치는 것을 처리하기 위해, 기본, 호버, 활성 상태에 대해 `1`, `2`, `3` 의 값을 `z-index` 값으로 사용합니다. 호버/포커스/활성 상태에서, 형제 요소 위에 테두리를 표시하기 위해 더 높은 `z-index` 값을 사용하여 특정 요소를 젤 앞으로 가져옵니다. 
