---
layout: docs
title: 그리드 시스템
description: 12 개의 컬럼 시스템, 5 가지 반응형 계층, Sass 변수 및 믹스인, 미리 정의된 많은 클래스들의 도움을 받아 다양한 형태와 크기의 레이아웃을 만들기 위해 강력한 모바일 우선 flexbox 그리드를 사용하세요.
group: layout
toc: true
---

## 작동 원리

부트스트랩의 그리드 시스템은 레이아웃을 만들고 콘텐츠를 정렬하는데 일련의 컨테이너, 행, 열을 사용합니다. 그것은 [flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes) 로 만들어졌으며 완전히 반응형입니다. 다음은 어떻게 그리드가 함께 나타나는지에 대한 예제와 심층적인 모습입니다. 

**flexbox 가 처음이거나 익숙하지 않으신가요?** 배경, 용어, 지침, 코드 조각 등을 위해 [CSS 트릭 웹사이트에서 flexbox 가이드를 읽어보세요](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#flexbox-background)

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col-sm">
      3열중 하나
    </div>
    <div class="col-sm">
      3열중 하나
    </div>
    <div class="col-sm">
      3열중 하나
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

위 예는 소형, 중형, 대형, 초대형 장치에서 미리 정의된 그리드 클래스를 사용하여 3 개의 같은 너비의 열을 생성합니다. 이 열들은 부모인 `.container` 와 함께 페이지 중앙에 배치됩니다.

세분화하면 다음과 같이 작동합니다.

- 컨테이너는 사이트의 콘텐츠를 중앙에 위치하게 하고 좌우로 패딩을 넣어주는 수단을 제공합니다. 반응형 픽셀 단위 너비를 위해서는 `.container` 를 사용하고, 모든 뷰포트와 장치 크기에 대해 `width: 100%` 를 위해서는 `.container-fluid` 를 사용하세요.
- 행은 열을 감쌉니다. 각 열은 그들 사이의 공간을 제어하기 위해 좌우로 `padding` (gutter 라고 불림) 이 있습니다. 이 `padding` 은 음수 마진을 가진 행과 대응됩니다. 이렇게 하면, 열의 모든 콘텐츠는 시각적으로 왼쪽으로 정렬됩니다.  
- 그리드 레이아웃에서, 콘텐츠는 열 내에 있어야 하고 열만이 행 바로 아래의 자식이 될 수 있습니다.
- flexbox 덕분에, `width` 를 지정하지 않은 그리드 열은 자동으로 같은 너비 열로 배치됩니다. 예를 들어, `.col-sm` 인스턴스 4개는 자동으로 소형 중단점 이상에서 25% 너비가 됩니다. 자세한 예제는 [auto-layout columns](#auto-layout-columns) 을 참조하세요.
- 열 클래스는 하나의 행마다 12 열중 사용하고 싶은 열의 수를 나타냅니다. 따라서, 만약 3 개의 동일한 너비의 열이 필요하다면 `.col-4` 를 사용할 수 있습니다.
- 열의 `width` 는 백분율로 설정되므로, 항상 부모 요소에 상대적으로 크기가 변경되고 유동적입니다. 
- 열들은 열사이에 홈을 만들기 위해 수평의 `padding` 을 가지고 있습니다만, 행의 `margin` 과 열의 `padding` 은 `.row` 에 `.no-gutters` 를 넣어 제거할 수 있습니다. 
- 그리드를 반응형을 만들기 위해 각 [반응형 중단점]({{ site.baseurl }}/docs/{{ site.docs_version }}/layout/overview/#반응형-중단점) 마다 하나씩 5가지 중단점이 있습니다. 중단점은 (초소형), 소형, 중형, 대형, 초대형 등이 있습니다.
- 그리드 중단점은 최소 너비 미디어 쿼리를 기반으로 합니다. 즉, **하나의 중단점과 그 이상에는 모두 적용됩니다** (예: `.col-sm-4` 은 소형, 중형, 대형, 초대형에 적용됩니다만, `xs` 중단점에는 적용되지 않습니다). 
- 더 시맨틱한 마크업을 위해 미리 정의된 (`.col-4` 과 같은) 그리드 클래스나 [Sass 믹스인](#sass-믹스인) 을 사용할 수 있습니다. 

[일부 HTML 요소는 flex 컨테이너로 사용할 수 없음](https://github.com/philipwalton/flexbugs#9-some-html-elements-cant-be-flex-containers) 과 같은 [flexbox 관련 버그](https://github.com/philipwalton/flexbugs) 와 한계를 알아두세요. 

## 그리드 옵션

부트스트랩은 대부분의 크기를 정의하기 위해 `em` 또는 `rem` 을 사용하지만, 그리드 중단점과 컨테이너 너비를 위해 `px` 를 사용합니다. 이것은 뷰포트 너비가 픽셀 단위이며 [글꼴 크기](https://drafts.csswg.org/mediaqueries-3/#units) 기반으로 변경되지 않기 때문입니다.

간단한 표를 통해서 다양한 장치에서 부트스트랩 그리드 시스템이 어떻게 작동하는지 살펴보세요.

<table class="table table-bordered table-striped">
  <thead>
    <tr>
      <th></th>
      <th class="text-center">
        초소형<br>
        <small>&lt;576px</small>
      </th>
      <th class="text-center">
        소형<br>
        <small>&ge;576px</small>
      </th>
      <th class="text-center">
        중형<br>
        <small>&ge;768px</small>
      </th>
      <th class="text-center">
        대형<br>
        <small>&ge;992px</small>
      </th>
      <th class="text-center">
        초대형<br>
        <small>&ge;1200px</small>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="text-nowrap" scope="row">최대 컨테이너 너비</th>
      <td>없음 (자동)</td>
      <td>540px</td>
      <td>720px</td>
      <td>960px</td>
      <td>1140px</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">클래스 접두사</th>
      <td><code>.col-</code></td>
      <td><code>.col-sm-</code></td>
      <td><code>.col-md-</code></td>
      <td><code>.col-lg-</code></td>
      <td><code>.col-xl-</code></td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">열 수</th>
      <td colspan="5">12</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">홈 너비</th>
      <td colspan="5">30px (열의 각 옆면에 15px)</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">중첩가능</th>
      <td colspan="5">예</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">열 순서정하기</th>
      <td colspan="5">예</td>
    </tr>
  </tbody>
</table>

## 자동 레이아웃 열

`.col-sm-6` 과 같이 명확히 숫자로된 클래스 없이 쉽게 열의 크기를 지정하기 위해서 중단점-명시 열 클래스를 이용하세요.

### 같은 너비

예를 들면, 다음은 `xs` 부터 `xl` 까지 모든 장치와 뷰포트에서 적용되는 2 가지 그리드 레이아웃입니다. 필요한 각 중단점에 단위없이 클래스를 추가하면 모든 열은 동일한 너비를 가지게 됩니다. 

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col">
      2 개중 1 번쨰
    </div>
    <div class="col">
      2 개중 2 번째
    </div>
  </div>
  <div class="row">
    <div class="col">
      3 개중 1 번째
    </div>
    <div class="col">
      3 개중 2 번째
    </div>
    <div class="col">
      3 개중 3 번째
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

같은 너비의 열은 여러 줄로 나눠질 수 있습니다만, 명시적인 `flex-basis` 나 `border` 없이 동작하는 것을 막는 [사파리 flexbox 버그](https://github.com/philipwalton/flexbugs#11-min-and-max-size-declarations-are-ignored-when-wrapping-flex-items) 가 있습니다. 오래된 브라우저 버전들을 위한 해결책이 있으나, 최신버전이라면 필요하지 않습니다. 

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col">열</div>
    <div class="col">열</div>
    <div class="w-100"></div>
    <div class="col">열</div>
    <div class="col">열</div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 특정 열 너비 설정하기

flexbox 를 위한 자동 레이아웃은 특정한 하나의 열 너비를 설정하면 형제 열들은 자동으로 그것에 맞춰 크기가 변경됩니다. 미리 정의된 그리드 클래스 (아래 참조), 그리드 믹스인, 인라인 너비 등을 사용할 수 있습니다. 다른 열의 크기가 변경되는데 가운데 열의 너비는 중요하지 않습니다. 

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col">
      3 개중 1 번째
    </div>
    <div class="col-6">
      3 개중 2 번째 (넓음)
    </div>
    <div class="col">
      3 개중 3번째
    </div>
  </div>
  <div class="row">
    <div class="col">
      3 개중 1 번째
    </div>
    <div class="col-5">
      3 개중 2 번째 (넓음)
    </div>
    <div class="col">
      3 개중 3 번째
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 가변폭 콘텐츠

콘텐츠의 너비에 따라 열의 크기를 조정하기 위해 `col-{breakpoint}-auto` 클래스를 사용하세요.

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row justify-content-md-center">
    <div class="col col-lg-2">
      3 개중 1 번째
    </div>
    <div class="col-md-auto">
      가변폭 콘텐츠
    </div>
    <div class="col col-lg-2">
      3 개중 3 번째
    </div>
  </div>
  <div class="row">
    <div class="col">
      3 개중 1 번째
    </div>
    <div class="col-md-auto">
      가변폭 콘텐츠
    </div>
    <div class="col col-lg-2">
      3 개중 3 번째
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 여러 행에서 같은 너비

줄바꿈하고 싶은 위치에 `.w-100` 를 넣어 여러 줄에 걸친 같은 너비의 열을 만들어 보세요. 일부 [반응형 디스플레이 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/display/) 와 `.w-100` 을 혼합하여 줄바꿈을 반응형으로 만들어보세요.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col">col</div>
  <div class="col">col</div>
  <div class="w-100"></div>
  <div class="col">col</div>
  <div class="col">col</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

## 반응형 클래스

부트스트랩의 그리드는 복잡한 반응형 레이아웃을 작성하기 위한 미리 정의된 클래스들 5 계층이 있습니다. 당신이 생각하는 대로 초소형, 소형, 중형, 대형, 초대형 장치 상의 열의 크기를 맞춤화할 수 있습니다.

### 모든 중단점

초소형 장치부터 초대형 장치까지 같은 그리드를 위해, `.col` 와 `.col-*` 을 사용하세요. 특별히 크기가 정해진 열이 필요할 때 숫자가 매겨진 클래스를 지정하시고, 보통 그냥 `.col` 을 사용하시면 됩니다. 

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col">col</div>
  <div class="col">col</div>
  <div class="col">col</div>
  <div class="col">col</div>
</div>
<div class="row">
  <div class="col-8">col-8</div>
  <div class="col-4">col-4</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 수직에서 수평으로

`.col-sm-*` 클래스를 사용하면, 수직으로 쌓이는 것에서 시작해서 소형 중단점 (`sm`) 부터 수평으로 되는 기본 그리드 시스템을 만들수 있습니다.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-sm-8">col-sm-8</div>
  <div class="col-sm-4">col-sm-4</div>
</div>
<div class="row">
  <div class="col-sm">col-sm</div>
  <div class="col-sm">col-sm</div>
  <div class="col-sm">col-sm</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 조합

일부 그리드 계층에서 열이 단순하게 쌓이는 것을 원하지 않습니까? 필요한 계층을 위해 다른 클래스의 조합을 사용해보세요. 어떻게 작동하는지 아이디어를 확인하려면 아래의 예제를 보세요.

<div class="bd-example-row">
{% capture example %}
<!-- 하나는 최대 너비, 다른 하나는 절반 너비를 지정하여 모바일에서 열이 수직으로 쌓이도록 한다 -->
<div class="row">
  <div class="col-12 col-md-8">.col-12 .col-md-8</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>

<!-- 열은 모바일에서는 50% 너비로 시작해서 데스크탑에서는 33.3% 가 됩니다 -->
<div class="row">
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>

<!-- 열은 모바일과 데스크탑에서 항상 50% 너비를 가집니다 -->
<div class="row">
  <div class="col-6">.col-6</div>
  <div class="col-6">.col-6</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

## 정렬

열을 수직 및 수평 정렬하기 위해 flexbox 정렬 유틸리티를 사용하세요.

### 수직 정렬

<div class="bd-example-row bd-example-row-flex-cols">
{% capture example %}
<div class="container">
  <div class="row align-items-start">
    <div class="col">
      세 열중 하나
    </div>
    <div class="col">
      세 열중 하나
    </div>
    <div class="col">
      세 열중 하나
    </div>
  </div>
  <div class="row align-items-center">
    <div class="col">
      세 열중 하나
    </div>
    <div class="col">
      세 열중 하나
    </div>
    <div class="col">
      세 열중 하나
    </div>
  </div>
  <div class="row align-items-end">
    <div class="col">
      세 열중 하나
    </div>
    <div class="col">
      세 열중 하나
    </div>
    <div class="col">
      세 열중 하나
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

<div class="bd-example-row bd-example-row-flex-cols">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col align-self-start">
      세 열중 하나
    </div>
    <div class="col align-self-center">
      세 열중 하나
    </div>
    <div class="col align-self-end">
      세 열중 하나
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 수평 정렬

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row justify-content-start">
    <div class="col-4">
      두 열중 하나
    </div>
    <div class="col-4">
      두 열중 하나
    </div>
  </div>
  <div class="row justify-content-center">
    <div class="col-4">
      두 열중 하나
    </div>
    <div class="col-4">
      두 열중 하나
    </div>
  </div>
  <div class="row justify-content-end">
    <div class="col-4">
      두 열중 하나
    </div>
    <div class="col-4">
      두 열중 하나
    </div>
  </div>
  <div class="row justify-content-around">
    <div class="col-4">
      두 열중 하나
    </div>
    <div class="col-4">
      두 열중 하나
    </div>
  </div>
  <div class="row justify-content-between">
    <div class="col-4">
      두 열중 하나
    </div>
    <div class="col-4">
      두 열중 하나
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### No gutters

미리 정의된 그리드 클래스 내의 열 사이에 홈은 `.no-gutters` 로 제거 될 수 있습니다. 이것은 `.row` 의 음수 `margin` 들과 모든 직계 하위 열들의 수평 `padding` 을 제거합니다.

다음은 이러한 스타일을 만드는 데 필요한 소스 코드입니다.
열 오버라이드는 첫번째 하위 열들에게만 적용되고 [속성 선택자](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) 을 통해 대상으로 지정됩니다.
더 구체적인 선택자를 작성한다면, 열 패딩은 [spacing 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/spacing/) 를 이용하여 추가적으로 맞춤화할 수 있습니다.

**Edge-to-edge 디자인이 필요하세요?** 부모 `.container` 나 `.container-fluid` 를 제거하세요.

{% highlight sass %}
.no-gutters {
  margin-right: 0;
  margin-left: 0;

  > .col,
  > [class*="col-"] {
    padding-right: 0;
    padding-left: 0;
  }
}
{% endhighlight %}

실제로 그것은 다음과 같이 보입니다. 미리 정의된 다른 그리드 클래스 (열 너비, 반응형 계층, 순서지정 등) 와 함께 계속 사용할 수 있습니다.

<div class="bd-example-row">
{% capture example %}
<div class="row no-gutters">
  <div class="col-12 col-sm-6 col-md-8">.col-12 .col-sm-6 .col-md-8</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 열 감싸기

하나의 행에 12 개 이상의 열이 있으면 하나의 단위를 기준으로 초과된 열을 가진 그룹은 새로운 행으로 감싸집니다.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-9">.col-9</div>
  <div class="col-4">.col-4<br>9 + 4 = 13 &gt; 12 이므로, 이 4 열 너비 div 는 인접된 단위로서 새로운 행으로 감싸집니다.</div>
  <div class="col-6">.col-6<br>후속 열은 새 행에 계속 이어집니다.</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 열 줄바꿈

flexbox 에서 새 행으로 열을 줄바꿈 하는 것은 약간의 꼼수가 필요합니다. 새 행으로 감싸고 싶은 열이 있다면 `width: 100%` 를 추가하세요. 보통 이것을 여러 개의 `.row` 로 해결하지만, 모든 구현을 그렇게 해결한다고는 할 수 없습니다.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>
  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>

  <!-- 다음 열을 강제로 새 행으로 줄바꿈합니다 -->
  <div class="w-100"></div>

  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>
  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

우리의 [반응형 디스플레이 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/display/) 를 사용해서 특정한 중단점에 이 줄바꿈을 적용할 수도 있습니다.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>
  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>

  <!-- 중형 중단점 이상에서 다음 열을 새로운 행으로 강제로 줄바꿈합니다 -->
  <div class="w-100 d-none d-md-block"></div>

  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>
  <div class="col-6 col-sm-4">.col-6 .col-sm-4</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

## 순서지정

### 순서 클래스

콘텐츠의 **시각적인 순서** 제어하기 위해서 `.order-` 클래스를 사용하세요. 이 클래스는 반응형이어서 중단점 (예: `.order-1.order-md-2`) 별로 `order` 를 설정할 수 있습니다. 순서지정은 5 그리드 계층에 대해 `1` 부터 `12` 까지 지원합니다. 

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col">
      첫번째이지만 순서는 지정되지 않음
    </div>
    <div class="col order-12">
      두번째이지만 순서는 마지막으로
    </div>
    <div class="col order-1">
      세번째이지만 순서는 첫번째로
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

`order: -1` 와 `order: 13` (`order: $columns + 1`) 을 적용하여 요소의 `order` 를 변경시키는 `.order-first` 와 `.order-last` 클래스도 있습니다. 이 클래스들은 필요한 경우 `.order-*` 와 섞일 수도 있습니다.

<div class="bd-example-row">
{% capture example %}
<div class="container">
  <div class="row">
    <div class="col order-last">
      첫번째이지만 순서는 마지막으로
    </div>
    <div class="col">
      두번째이지만 순서는 지정되지 않음
    </div>
    <div class="col order-first">
      세번째이지만 순서는 첫번째로
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

### 열 오프셋

반응형 `.offset-` 그리드 클래스와 [여백 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/spacing/) 등 2가지 방법으로 그리드 컬럼간의 오프셋을 지정할 수 있습니다. 그리드 클래스는 열에 맞추어 크기가 조정되는 반면에 margin 은 오프셋의 너비가 다양한 레이아웃에 더 유용합니다.

#### 오프셋 클래스

`.offset-md-*` 클래스를 사용하여 열을 오른쪽으로 옮기세요. 이 클래스들은 컬럼의 왼쪽 여백을 `*` 열만큼 늘립니다. 예를 들어, `.offset-md-4` 은 `.col-md-4` 을 4 열만큼 옮깁니다. 

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4 offset-md-4">.col-md-4 .offset-md-4</div>
</div>
<div class="row">
  <div class="col-md-3 offset-md-3">.col-md-3 .offset-md-3</div>
  <div class="col-md-3 offset-md-3">.col-md-3 .offset-md-3</div>
</div>
<div class="row">
  <div class="col-md-6 offset-md-3">.col-md-6 .offset-md-3</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

추가로 반응형 중단점에서 오프셋을 재설정하는 것이 필요할 수도 있습니다. [그리드 예제]({{ site.baseurl }}/docs/{{ site.docs_version }}/examples/grid/) 에서 실제로 확인해 보세요.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-sm-5 col-md-6">.col-sm-5 .col-md-6</div>
  <div class="col-sm-5 offset-sm-2 col-md-6 offset-md-0">.col-sm-5 .offset-sm-2 .col-md-6 .offset-md-0</div>
</div>

<div class="row">
  <div class="col-sm-6 col-md-5 col-lg-6">.col-sm-6 .col-md-5 .col-lg-6</div>
  <div class="col-sm-6 col-md-5 offset-md-2 col-lg-6 offset-lg-0">.col-sm-6 .col-md-5 .offset-md-2 .col-lg-6 .offset-lg-0</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

#### 여백 유틸리티

v4 의 flexbox 로 옮겨 가면서, `.mr-auto` 와 같은 여백 유틸리티를 사용하면 형제 열들을 서로 멀리 떨어뜨릴 수 있습니다.

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4 ml-auto">.col-md-4 .ml-auto</div>
</div>
<div class="row">
  <div class="col-md-3 ml-md-auto">.col-md-3 .ml-md-auto</div>
  <div class="col-md-3 ml-md-auto">.col-md-3 .ml-md-auto</div>
</div>
<div class="row">
  <div class="col-auto mr-auto">.col-auto .mr-auto</div>
  <div class="col-auto">.col-auto</div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

## 중첩

콘텐츠를 기본 그리드로 중첩하려면, `.col-sm-*` 열에 새로운 `.row` 와 `.col-sm-*` 열들을 추가하세요. 중첩된 행들은 최대 12 개 이하의 열 세트를 포함해야 합니다 (사용가능한 12 개의 열을 모두 사용할 필요는 없습니다).

<div class="bd-example-row">
{% capture example %}
<div class="row">
  <div class="col-sm-9">
    Level 1: .col-sm-9
    <div class="row">
      <div class="col-8 col-sm-6">
        Level 2: .col-8 .col-sm-6
      </div>
      <div class="col-4 col-sm-6">
        Level 2: .col-4 .col-sm-6
      </div>
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}
</div>

## Sass 믹스인

부트스트랩의 Sass 소스 파일을 사용할 때 Sass 변수와 믹스인을 사용하여 맞춤화, 시맨틱, 반응형 페이지 레이아웃을 생성할 수 있습니다. 미리 정의된 그리드 클래스는 이와 같은 변수와 믹스인을 이용하여 빠른 반응형 레이아웃을 위해 바로 사용될 수 있는 클래스 모음을 제공합니다.

### 변수

변수와 맵은 열의 수, 홈의 너비, 부동형 열을 시작하는 미디어 쿼리 포인트 등을 결정합니다. 우리는 아래에 나열된 맞춤 믹스인뿐만 아니라 앞서 설명한 미리 정의된 그리드 클래스를 생성하기 위해 이것들을 사용합니다.

{% highlight scss %}
$grid-columns:      12;
$grid-gutter-width: 30px;

$grid-breakpoints: (
  // 초소형 화면 / 휴대폰
  xs: 0,
  // 소형 화면 / 휴대폰
  sm: 576px,
  // 중형 화면 / 태블릿
  md: 768px,
  // 대형 화면 / 데스크탑
  lg: 992px,
  // 초대형 화면 / 큰 데스크탑
  xl: 1200px
);

$container-max-widths: (
  sm: 540px,
  md: 720px,
  lg: 960px,
  xl: 1140px
);
{% endhighlight %}

### 믹스인

믹스인은 그리드 변수와 함께 사용되어 개별 그리드 열에 대해 시맨틱 CSS 를 생성합니다.

{% highlight scss %}
// 일련의 열을 감싸는 row 를 만듭니다
@include make-row();

// grid-ready 요소를 만듭니다 (너비를 제외한 모든 것)
@include make-col-ready();
@include make-col($size, $columns: $grid-columns);

// 오프셋을 사용하거나 정렬 순서를 바꾸어 멋지게 표현해보세요
@include make-col-offset($size, $columns: $grid-columns);
{% endhighlight %}

### 사용예

변수를 맞춤 값으로 수정하거나 기본값을 사용하여 믹스인을 사용할 수 있습니다. 다음은 기본 설정을 사용하여 간격이 있는 두 열 레이아웃을 만드는 예입니다.

{% highlight scss %}
.example-container {
  width: 800px;
  @include make-container();
}

.example-row {
  @include make-row();
}

.example-content-main {
  @include make-col-ready();

  @include media-breakpoint-up(sm) {
    @include make-col(6);
  }
  @include media-breakpoint-up(lg) {
    @include make-col(8);
  }
}

.example-content-secondary {
  @include make-col-ready();

  @include media-breakpoint-up(sm) {
    @include make-col(6);
  }
  @include media-breakpoint-up(lg) {
    @include make-col(4);
  }
}
{% endhighlight %}

{% capture example %}
<div class="example-container">
  <div class="example-row">
    <div class="example-content-main">메인 콘텐츠</div>
    <div class="example-content-secondary">보조 콘텐츠</div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

## 그리드 맞춤화

내장된 그리드 Sass 변수와 맵을 사용하여 미리 정의 된 그리드 클래스를 완벽하게 맞춤화 할 수 있습니다. 계층 수, 미디어 쿼리 수치, 컨테이너 너비를 변경 한 다음 다시 컴파일하십시오.

### 열과 홈

그리드 열 수는 Sass 변수를 통해 수정될 수 있습니다. `$grid-columns` 는 각각의 개별 열의 너비 (백분율) 를 생성하는데 사용되는 반면 `$grid-gutter-width` 는 열의 홈을 위한 `padding-left` 와 `padding-right` 에 걸쳐 균등하게 나뉘는 중단점 지정 너비를 허용합니다.

{% highlight scss %}
$grid-columns: 12 !default;
$grid-gutter-width: 30px !default;
{% endhighlight %}

### 그리드 계층

열을 맞춤화하는 것을 넘어, 그리드 계층의 수를 맞춤화 할 수도 있습니다. 만약 4 개의 그리드 계층을 원한다면, `$grid-breakpoints` 와 `$container-max-widths` 를 다음과 같이 갱신 할 것입니다.

{% highlight scss %}
$grid-breakpoints: (
  xs: 0,
  sm: 480px,
  md: 768px,
  lg: 1024px
);

$container-max-widths: (
  sm: 420px,
  md: 720px,
  lg: 960px
);
{% endhighlight %}

Sass 변수나 맵을 변경할 때, 변경사항을 저장하고 다시 컴파일 해야합니다. 이렇게 하면 열 너비, 오프셋, 순서정하기를 위한 미리 정의된 그리드 클래스 묶음이 새롭게 산출됩니다. 또한 반응형 가시성 유틸리티는 맞춤 중단점을 사용하도록 갱신될 것입니다. 그리드 값들은 `px` 로 설정해야함을 명심하세요. (`rem`, `em`, `%` 아님)
