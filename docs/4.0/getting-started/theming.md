---
layout: docs
title: 테마
description: 쉬운 테마와 컴포넌트 변경을 위해 전역 스타일 환경 설정을 위해 새롭게 내장된 Sass 변수로 부트스트랩 4 를 맞춤화하세요.
group: getting-started
toc: true
redirect_from: "/docs/4.0/getting-started/options/"
---

## 소개

부트스트랩 3 에서 테마 꾸미기는 LESS, 맞춤 CSS, `dist` 파일에 포함된 별도의 테마 스타일시트에서 맞춤 변수 오버라이드에 의해 크게 좌우되었습니다. 약간의 수고로, 부트스트랩의 형태를 코어 파일을 건드리지 않도록 완전히 다시 설계하였습니다. 부트스트랩 4 는 친숙하지만, 약간 다른 접근 방법으로 제공합니다.

이제, 테마 꾸미기는 Sass 변수, Sass 맵, 맞춤 CSS 로 완수할 수 있습니다. 더이상 전용 테마 스타일시트는 없습니다. 대신, 내장된 테마의 그래디언트, 그림자 등을 활성할 수 있습니다.

## Sass

변수, 맵, 믹스인 등의 이점을 가져가려면 Sass 소스 파일을 활용하세요.

### 파일 구조

가능한, 부트스트랩의 코어 파일을 수정하는 것은 피해주세요. Sass 의 경우, 부트스트랩을 가져와서 자신만의 스타일시트를 만들어 수정하고 확장할 수 있습니다. npm 과 같은 패키지 관리자를 사용한다고 가정하면, 당신은 다음과 같은 파일 구조를 가질 것입니다.

{% highlight plaintext %}
your-project/
├── scss
│   └── custom.scss
└── node_modules/
    └── bootstrap
        ├── js
        └── scss
{% endhighlight %}

만약 우리의 소스 파일을 패키지 관리자를 사용하지 않고 다운로드했다면, 부트스트랩과 당신의 소스를 구분하기 위해, 아래 구조와 비슷하게 구성하길 원할 것입니다.

{% highlight plaintext %}
your-project/
├── scss
│   └── custom.scss
└── bootstrap/
    ├── js
    └── scss
{% endhighlight %}

### 가져오기

당신의 `custom.scss` 에서, 부트스트랩의 Sass 파일을 가져올 것입니다. 두가지 선택사항이 있습니다: 부트스트랩의 모든 것을 포함하거나, 필요한 부분만 골라 포함할 수 있습니다. 우리는 후자를 장려합니다만, 컴포넌트 사이에는 약간의 요구조건과 의존성이 있음을 유의하세요. 또한 플러그인을 위한 일부 자바스크립트를 포함하는 것이 필요할 것입니다. 

{% highlight scss %}
// Custom.scss
// 선택사항 A: 부트스트랩 전부를 포함

@import "node_modules/bootstrap/scss/bootstrap";
{% endhighlight %}

{% highlight scss %}
// Custom.scss
// 선택사항 B: 부트스트랩 일부를 포함

// 필수
@import "node_modules/bootstrap/scss/functions";
@import "node_modules/bootstrap/scss/variables";
@import "node_modules/bootstrap/scss/mixins";

// 선택
@import "node_modules/bootstrap/scss/reboot";
@import "node_modules/bootstrap/scss/type";
@import "node_modules/bootstrap/scss/images";
@import "node_modules/bootstrap/scss/code";
@import "node_modules/bootstrap/scss/grid";
{% endhighlight %}

이 설정을 통해, `custom.scss` 에서 Sass 변수와 맵을 수정할 수 있습니다. 필요한 경우 부트스트랩의 일부를 `// 선택` 섹션 아래에 추가할 수도 있습니다. 처음에는 `bootstrap.scss` 파일을 가져와 전부를 사용하는 것을 추천합니다.

### 변수 기본값

부트스트랩 4 에서 모든 Sass 변수는 부트스트랩의 소스 코드를 수정하지 않고 당신만의 Sass 에서 변수를 기본값을 오버라이드할 수 있도록 `!default` 플래그를 포함합니다. 필요한 변수를 복사하여 붙여넣고, 값을 수정하고, `!default` 플래그를 제거하세요. 만약 변수가 이미 할당되었다면, 부트스트랩의 기본값으로 재할당되지 않을 것입니다.

부트스트랩의 변수들의 목록 전부를 `scss/_variables.scss` 에서 찾을 수 있습니다.

같은 Sass 파일내에서 변수 오버라이드는 기본 변수 앞이나 뒤에 올 수 있습니다. 하지만, Sass 파일들간에 오버라이드할때는, 가져온 부트스트랩의 Sass 파일보다 앞에 오버라이드가 와야 합니다.

여기 npm 을 통해 부트스트랩을 컴파일하고 가져왔을때 `<body>` 의 `background-color` 와 `color` 를 변경한 예제가 있습니다.

{% highlight scss %}
// 당신의 변수 오버라이드
$body-bg: #000;
$body-color: #111;

// 부트스트랩과 기본 변수들
@import "node_modules/bootstrap/scss/bootstrap";
{% endhighlight %}

아래의 전역 옵션을 포함하여 부트스트랩의 어떤 변수도 똑같이 하면 됩니다.

### 맵

부트스트랩 4 에는 관련된 CSS 의 계열을 쉽게 생성할 수 있게 해주는 약간의 Sass 맵, 키 값 쌍이 포함됩니다. 색상, 그리드 중단점 등에 Sass 맵을 사용합니다. Sass 변수와 마찬가지로 모든 Sass 맵은 `!default` 플래그를 포함하고 오버라이드하거나 확장될 수 있습니다.

일부 Sass 맵은 기본적으로 빈 맵으로 병합됩니다. 이는 주어진 Sass 맵을 쉽게 확장할 수 있도록 하기 위함이지만 맵에서 항목을 _제거하는 것_ 이 약간 더 어려워졌습니다.

#### 맵 수정하기

`$theme-colors` 맵에서 기존의 색을 수정하려면, 다음을 맞춤 Sass 파일에 추가하세요.

{% highlight scss %}
$theme-colors: (
  "primary": #0074d9,
  "danger": #ff4136
);
{% endhighlight %}

#### 맵에 추가하기

`$theme-colors` 에 새로운 색을 추가하려면, 새로운 키와 값을 추가하세요.

{% highlight scss %}
$theme-colors: (
  "custom-color": #900
);
{% endhighlight %}

#### 맵에서 제거하기

`$theme-colors` 또는 다른 맵에서 색을 제거하려면, `map-remove` 을 사용하세요. 필수와 선택 사이에 넣어야 함을 유의하세요.

{% highlight scss %}
// 필수
@import "node_modules/bootstrap/scss/functions";
@import "node_modules/bootstrap/scss/variables";
@import "node_modules/bootstrap/scss/mixins";

$theme-colors: map-remove($theme-colors, "info", "light", "dark");

// 선택
@import "node_modules/bootstrap/scss/root";
@import "node_modules/bootstrap/scss/reboot";
@import "node_modules/bootstrap/scss/type";
...
{% endhighlight %}

#### 키

부트스트랩은 우리가 사용하고 확장한 Sass 맵에 특정 키가 있다고 가정합니다. 포함된 맵을 맞춤화하면 특정 Sass 맵의 키가 사용되어 지는 곳에서 에러가 발생할 수 있습니다.

예를 들면, 링크, 버튼, 폼 상태에 대해 `$theme-colors` 에서 `primary`, `success`, `danger` 키들을 사용합니다. 이 키들을 교체하는 것은 문제가 되지 않지만, 제거하는 것은 Sass 컴파일 문제를 야기할 수 있습니다. 이러한 경우, 해당 값을 사용하는 Sass 코드를 수정해야 합니다.

### 함수

부트스트랩은 여러 Sass 함수를 사용하지만, 일부만이 테마 꾸미는데 적용됩니다. 색상 맵에서 값을 가져오는 것에 3가지 함수가 포함되어 있습니다.

{% highlight scss %}
@function color($key: "blue") {
  @return map-get($colors, $key);
}

@function theme-color($key: "primary") {
  @return map-get($theme-colors, $key);
}

@function gray($key: "100") {
  @return map-get($grays, $key);
}
{% endhighlight %}

이를 통해 v3 의 색상 변수를 사용하는 것과 같은 방법으로 Sass 맵에서 하나의 색을 뽑아낼 수 있습니다.

{% highlight scss %}
.custom-element {
  color: gray("100");
  background-color: theme-color("dark");
}
{% endhighlight %}

우리는 또한 `$theme-colors` 맵으로부터 색상의 특정한 _레벨_ 을 가져오는 함수를 가지고 있습니다. 음수 레벨 값은 색상을 밝게 하는 반면, 높은 레벨은 어두워집니다.

{% highlight scss %}
@function theme-color-level($color-name: "primary", $level: 0) {
  $color: theme-color($color-name);
  $color-base: if($level > 0, #000, #fff);
  $level: abs($level);

  @return mix($color-base, $color, $level * $theme-color-interval);
}
{% endhighlight %}

실제에 있어서, 당신은 함수를 호출하고 `$theme-colors` 의 색이름(예: primary 나 danger)과 레벨 등 2가지 파라미터를 전달합니다.

{% highlight scss %}
.custom-element {
  color: theme-color-level(primary, -10);
}
{% endhighlight %}

추가 함수는 장래에 추가될 수 있고, 자신의 맞춤 Sass 에 추가적인 Sass 맵을 위한 레벨 함수를 생성 할 수도 있고, 좀 더 장황한 것을 원한다면 일반적인 함수를 만들수도 있습니다.

### 색상 대비

우리가 포함한 추가 함수는 색상 대비 함수, `color-yiq` 입니다. [YIQ 색 공간](https://en.wikipedia.org/wiki/YIQ) 을 사용하여 특정한 기본 색상을 기본으로 하여 밝거나 (`#fff`) 어두운 (`#111`) 대조 색을 자동으로 반환합니다. 이 함수는 여러 클래스를 생성하는 믹스인이나 반복문에서 특히 유용합니다.

예를 들어, `$theme-colors` 맵으로부터 색상 견본을 생성하려면:  

{% highlight scss %}
@each $color, $value in $theme-colors {
  .swatch-#{$color} {
    color: color-yiq($value);
  }
} 
{% endhighlight %}

또한 1회성으로도 쓰일 수 있습니다.

{% highlight scss %}
.custom-element {
  color: color-yiq(#000); // returns `color: #fff`
}
{% endhighlight %}

컬러 맵 함수를 통해 기본 색상을 지정할 수 도 있습니다.

{% highlight scss %}
.custom-element {
  color: color-yiq(theme-color("dark")); // returns `color: #fff`
}
{% endhighlight %}

## Sass 옵션

내장된 맞춤 변수 파일로 부트스트랩 4 를 맞춤 설정하고 새로운 `$enable-*` Sass 변수로 전역 CSS 환경 설정을 쉽게 토글할 수 있습니다. 변수값을 오버라이드하고 필요에 따라 `npm run test` 을 사용하여 다시 컴파일하세요.

부트스트랩의 `scss/_variables.scss` 파일에서 핵심 전역 옵션을 위한 변수들을 찾아서 맞춤화할 수 있습니다.

| 변수                        | 값                                 | 설명                                                                                   |
| --------------------------- | ---------------------------------- | -------------------------------------------------------------------------------------- |
| `$spacer`                   | `1rem` (기본값), 이거나 모든값 > 0 | [공백 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/spacing/) 을 이용해서 프로그래밍 방식으로 생성하기 위한 기본 공백 크기값을 지정합니다. |
| `$enable-rounded`           | `true` (기본값) 이거나 `false`        | 다양한 컴포넌트에 미리 정의된 `border-radius` 스타일을 활성화합니다. |
| `$enable-shadows`           | `true` 이거나 `false` (기본값)        | 다양한 컴포넌트에 미리 정의된 `box-shadow` 스타일을 활성화합니다. |
| `$enable-gradients`         | `true` 이거나 `false` (기본값)        | 다양한 컴포넌트에 `background-image` 스타일을 미리 정의된 그라데이션을 활성화합니다. |
| `$enable-transitions`       | `true` (기본값) 이거나 `false`        | 다양한 컴포넌트에 미리 정의된 `transition` 을 활성화합니다. |
| `$enable-hover-media-query` | `true` 이거나 `false` (기본값)        | **폐기됨** |
| `$enable-grid-classes`      | `true` (기본값) 이거나 `false`        | 그리드 시스템 용 CSS 클래스 (예: `.container`, `.row`, `.col-md-1` 등) 를 생성할 수 있도록 합니다. |
| `$enable-caret`             | `true` (기본값) 이거나 `false`        | `.dropdown-toggle` 에서 캐럿을 활성화합니다. |
| `$enable-print-styles`      | `true` (기본값) 이거나 `false`        | 인쇄 최적화를 위한 스타일을 활성화합니다. |

## 색상

부트스트랩의 다양한 컴포넌트와 유틸리티는 Sass 맵에 정의된 일련의 색상을 통해 만들어집니다. 이 맵은 일련의 규칙 집합을 빠르게 생성하기 위해 반복될 수 있습니다.

### 모든 색상

부트스트랩 4 에서 사용할 수 있는 모든 색상은 `scss/_variables.scss` 파일에서 Sass 변수와 Sass 맵으로 사용할 수 있습니다. 이것은 이미 포함되어 있는 [그레이스케일 팔레트](#회색) 와 같이 추가 음영을 추가하기 위한 다음 마이너 버전에서 확장 될 것입니다.

<div class="row">
  {% for color in site.data.colors %}
    {% unless color.name == "white" or color.name == "gray" or color.name == "gray-dark" %}
    <div class="col-md-4">
        <div class="p-3 mb-3 swatch-{{ color.name }}">{{ color.name | capitalize }}</div>
    </div>
    {% endunless %}
  {% endfor %}
</div>

Sass 에서 이것을 사용하는 방법은 다음과 같습니다.

{% highlight scss %}
// 변수로
.alpha { color: $purple; }

// `color()` 함수와 함께 Sass 맵에서
.beta { color: color("purple"); }
{% endhighlight %}

[색상 유틸리티 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/colors/) 는 또한 `color` 와 `background-color` 를 설정하기 위해 사용할 수 있습니다.

{% capture callout %}
앞으로는 그레이스케일 색상을 사용한 것처럼 각 색상의 음영에 Sass 맵과 변수를 제공하는 것을 목표로 할 것입니다.
{% endcapture %}
{% include callout.html content=callout type="info" %}

### 테마 색상

우리는 모든 색상의 하위 집합을 사용하여 색 구성표를 생성하기 위한 작은 색상표를 만들고 부트스트랩의 `scss / _variables.scss` 파일에서 Sass 변수와 Sass 맵으로 사용할 수도 있습니다.

<div class="row">
  {% for color in site.data.theme-colors %}
    <div class="col-md-4">
      <div class="p-3 mb-3 swatch-{{ color.name }}">{{ color.name | capitalize }}</div>
    </div>
  {% endfor %}
</div>

### 회색

프로젝트 전체에 일관된 회색 음영을 위한 `scss / _variables.scss` 의 회색 변수와 Sass 맵의 확장 세트.

<div class="row mb-3">
  <div class="col-md-4">
    {% for color in site.data.grays %}
      <div class="p-3 swatch-{{ color.name }}">{{ color.name | capitalize }}</div>
    {% endfor %}
  </div>
</div>

`scss/_variables.scss` 안에 부트스트랩의 색상 변수와 Sass 맵이 있습니다. 다음은 Sass 맵 `$colors` 의 예시입니다.

{% highlight scss %}
$colors: (
  "blue": $blue,
  "indigo": $indigo,
  "purple": $purple,
  "pink": $pink,
  "red": $red,
  "orange": $orange,
  "yellow": $yellow,
  "green": $green,
  "teal": $teal,
  "cyan": $cyan,
  "white": $white,
  "gray": $gray-600,
  "gray-dark": $gray-800
) !default;
{% endhighlight %}

다른 많은 컴포넌트에 사용되는 방식을 업데이트 하기 위해 맵내의 값을 추가, 제거 또는 수정하세요. 불행하게도 현재 _모든_ 컴포넌트가 Sass 맵을 사용하는 것은 아닙니다. 향후 업데이트는 이를 개선하기 위해 노력할 것입니다. 그때까지, `${color}` 변수와 Sass 맵을 사용하도록 하세요.

## 컴포넌트

부트스트랩의 많은 컴포넌트와 유틸리티는 Sass 맵을 반복하는 `@each` 로프로 만들어집니다. 이것은 우리의 `$theme-colors` 에 의해 다양한 컴포넌트의 변형을 만들고 중단점에 따라 반응형 변형을 생성하는데 특히 유용합니다. 이 Sass 맵을 맞춤화하고 다시 컴파일한다면, 이 루프에 반영된 변경 사항을 확인할 수 있습니다.

### 수식

부트스트랩의 많은 컴포넌트는 기본 수식 클래스 접근으로 만들어집니다. 이것은 기본 클래스에 스타일의 대부분이 포함되어 있고 수식 클래스의 스타일 변형을 한정되어 있음을 의미합니다. 이 수식 클래스는 우리의 수식 클래스의 수와 이름을 맞춤화하기 위해 `$theme-colors` 맵으로 만들어집니다.

`.alert` 컴포넌트와 `.bg-*` 배경 유틸리티에 수식자를 생성하기 위해 `$theme-colors` 맵을 반복하는 방식의 2가지 예가 있습니다.

{% highlight scss %}
// 알림 수식 클래스를 생성합니다
@each $color, $value in $theme-colors {
  .alert-#{$color} {
    @include alert-variant(theme-color-level($color, -10), theme-color-level($color, -9), theme-color-level($color, 6));
  }
}

// `.bg-*` 색상 유틸리티를 생성합니다
@each $color, $value in $theme-colors {
  @include bg-variant('.bg-#{$color}', $value);
}
{% endhighlight %}

### 반응형

이러한 Sass 루프는 색상 맵에만 국한되지 않습니다. 컴포넌트나 유틸리티의 반응형 변형도 생성할 수 있습니다. Sass 맵 `$grid-breakpoints` 을 이용한 `@each` 루프와 미디어 쿼리를 같이 사용한 반응형 텍스트 정렬 유틸리티를 예를 들어 보겠습니다.

{% highlight scss %}
@each $breakpoint in map-keys($grid-breakpoints) {
  @include media-breakpoint-up($breakpoint) {
    $infix: breakpoint-infix($breakpoint, $grid-breakpoints);

    .text#{$infix}-left   { text-align: left !important; }
    .text#{$infix}-right  { text-align: right !important; }
    .text#{$infix}-center { text-align: center !important; }
  }
}
{% endhighlight %}

`$grid-breakpoints` 을 수정해야 한다면, 그 맵을 반복하는 모든 루프에 변경 사항이 적용됩니다.

## CSS 변수

부트스트랩 4 에는 컴파일된 CSS 안에 20개 넘는 [CSS 맞춤 속성 (변수)](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables) 가 포함되어 있습니다. 브라우저 검사기, 코드 샌드박스, 일반 프로토타이핑 에서 작업할 때 테마 색상, 중단점, 주요 글꼴 스택과 같이 일반적으로 사용되는 값에 쉽게 접근할 수 있습니다.

### 가능한 변수

여기에 우리가 포함하는 변수가 있습니다 (`:root` 가 필요합니다). 그것들은 `_root.scss` 파일에 있습니다.

{% highlight css %}
:root {
  --blue: #007bff;
  --indigo: #6610f2;
  --purple: #6f42c1;
  --pink: #e83e8c;
  --red: #dc3545;
  --orange: #fd7e14;
  --yellow: #ffc107;
  --green: #28a745;
  --teal: #20c997;
  --cyan: #17a2b8;
  --white: #fff;
  --gray: #6c757d;
  --gray-dark: #343a40;
  --primary: #007bff;
  --secondary: #6c757d;
  --success: #28a745;
  --info: #17a2b8;
  --warning: #ffc107;
  --danger: #dc3545;
  --light: #f8f9fa;
  --dark: #343a40;
  --breakpoint-xs: 0;
  --breakpoint-sm: 576px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 992px;
  --breakpoint-xl: 1200px;
  --font-family-sans-serif: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  --font-family-monospace: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
}
{% endhighlight %}

### 예제

CSS 변수는 Sass 변수와 비슷한 유연성을 제공하지만, 브라우저에 제공 되기 전에 컴파일이 필요 없습니다. 예를 들면, 여기에서는 페이지의 글꼴과 링크 스타일을 CSS 변수로 재설정합니다.

{% highlight css %}
body {
  font: 1rem/1.5 var(--font-family-sans-serif);
}
a {
  color: var(--blue);
}
{% endhighlight %}

CSS 변수에 중단점을 포함하지만, 불행히도 미디어 쿼리에는 사용될 수 없습니다. 이들은 자바스크립트에 의해 활용될 수 있기 때문에 하위 호환성을 위해 컴파일된 CSS 로 남아 있습니다. [스펙 자세히 알아보기](https://www.w3.org/TR/css-variables-1/#using-variables)

