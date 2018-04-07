---
layout: docs
title: 자바스크립트
description: jQuery 를 기반하는 자바스크립트 플러그인을 이용해서 부트스트랩에 활력을 불어넣으세요. 각 플러그인, 데이터 및 프로그램밍 API 옵션, 기타 등에 대해 배워보세요.
group: getting-started
toc: true
---

## 개별적이거나 컴파일된

플러그인은 개별적으로 포함되거나 (부트스트랩의 개별적인 `*.js` 파일을 사용), `bootstrap.js` 를 사용하여 한번에 모두를 포함하거나, 압축된 `bootstrap.min.js` 을 포함할 수 있습니다. (동시에 포함하지 마세요) 

## 의존성

일부 플러그인과 CSS 컴포넌트는 다른 플러그인에 의존합니다. 개별적으로 플러그인을 포함하려 한다면, 설명서에서 이들의 의존성을 확인해야함을 명심하세요. 또한 **모든 플러그인은 jQuery 에 의존함** 을 기억하세요. (jQuery 는 반드시 플러그인 파일 **이전에** 포함되어야 한다는 것을 의미합니다) jQuery 의 어떤 버전이 지원되는지 보려면 [`package.json` 를 참고하세요]({{ site.repo }}/blob/v{{ site.current_version }}/package.json)

또한 드롭다운, 팝오버, 툴팁은 [Popper.js](https://popper.js.org/) 에 의존합니다.

## Data 속성

거의 모든 부트스트랩 플러그인은 data 속성을 이용해서 HTML 만으로 활성화하고 설정할 수 있습니다. (자바스크립트 기능성을 사용하기 위해 선호하는 방식) **하나의 요소에는 하나의 data 속성 세트를 사용할 수 있음** 을 명심하세요. (예를 들면, 같은 버튼에서 툴팁과 모달을 작동시킬 수 없습니다) 

하지만, 경우에 따라 이 기능을 끄는 것이 바람직할 수 있습니다. data 속성 API 를 비활성화하려면, document 에서 네임스페이스가 `data-api` 인 모든 이벤트를 끄세요.

{% highlight js %}
$(document).off('.data-api')
{% endhighlight %}

그렇지 않고, 특정한 플러그인만 끄려면, 다음과 같이 data-api 네임스페이스와 함께 플러그인 이름을 포함하시면 됩니다.

{% highlight js %}
$(document).off('.alert.data-api')
{% endhighlight %}

{% capture callout %}
##### 셀렉터 예외문자
`collapse:Example` 처럼 셀렉터에 예외문자를 사용하다면, 그것들을 반드시 escape 해야합니다. 왜냐하면 그것들은 jQuery 를 통해 전달되기 때문입니다.
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## 이벤트

부트스트랩은 대부분 플러그인의 고유한 동작에 맞춤 이벤트를 제공합니다. 일반적으로, 이것들은 동사원형이나 과거완료형입니다. 동사원형 (예: `show`) 은 이벤트의 시작에 실행되고, 과거완료형 (예: `shown`) 은 동작의 완료에 실행됩니다.

모든 동사원형 이벤트는 [`preventDefault()`](https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault) 기능을 제공합니다. 이것은 동작이 시작하기 전에 실행을 막을수 있는 기능을 제공합니다. 이벤트 핸들러에서 false 를 리턴하는 것도 또한 자동으로 `preventDefault()` 를 호출할 것입니다.   

{% highlight js %}
$('#myModal').on('show.bs.modal', function (e) {
  if (!data) return e.preventDefault() // 모달이 보여지는 것을 중지시킵니다.
})
{% endhighlight %}

## 프로그래밍 API

우리는 또한 당신이 모든 부트스트랩 플러그인을 완전히 자바스크립트 API 를 통해 사용할 수 있을거라고 생각합니다. 모든 공용 API 들은 단수이고, 연결가능한 메서드이며, 콜렉션을 리턴합니다.

{% highlight js %}
$('.btn.danger').button('toggle').addClass('fat')
{% endhighlight %}

모든 메서드는 선택적으로 옵션 개체를 넣거나 특별한 메서드를 대상으로 하는 문자열을 넣을 수도 있고, 아무것도 넣지 않을 수도 있습니다 (기본 동작으로 플러그인을 초기화함)

{% highlight js %}
$('#myModal').modal()                      // initialized with defaults
$('#myModal').modal({ keyboard: false })   // initialized with no keyboard
$('#myModal').modal('show')                // initializes and invokes show immediately
{% endhighlight %}

각 플러그인은 또한 `Constructor` 속성 (`$.fn.popover.Constructor`) 에서 생성자 코드를 볼 수 있습니다. 만약 특정 인스턴스를 얻고 싶다면, 요소로부터 직접 그것을 가져올 수 있습니다. `$('[rel="popover"]').data('popover')`

### 비동기 함수와 전환

모든 프로그래밍 API 메서드는 **비동기적** 이고 전환이 시작되면 **끝나기 전에** 호출자에게 반환합니다.

전환이 완료되었을 때 동작을 실행하기 위해, 해당되는 이벤트에 수신 대기할 수 있습니다.

{% highlight js %}
$('#myCollapse').on('shown.bs.collapse', function (e) {
  // 접히는 영역이 펴졌을때 실행할 동작
})
{% endhighlight %}

추가적으로 **전환하고 있는 컴포넌트에 메서드를 호출하는 것은 무시될 것입니다**.

{% highlight js %}
$('#myCarousel').on('slid.bs.carousel', function (e) {
  $('#myCarousel').carousel('2') // 슬라이드 1 로 전환이 완료되면 2 로 넘어갑니다
})

$('#myCarousel').carousel('1') // 슬라이드 1 로 넘어가기 시작하고 호출자에게 반환합니다
$('#myCarousel').carousel('2') // !! 슬라이드 1 로 전환이 끝나지 않았기 때문에 무시될 것입니다 !!
{% endhighlight %}

### 기본 설정

플러그인의 `Constructor.Default` 개체를 수정하여 플러그인에 대한 기본 설정을 변경할 수 있습니다.

{% highlight js %}
$.fn.modal.Constructor.Default.keyboard = false // 모달 플러그인의 `keyboard` 옵션을 false 를 기본으로 변경합니다
{% endhighlight %}

## 충돌 방지

가끔 부트스트랩 플러그인을 다른 UI 프레임워크와 같이 사용할 필요가 있습니다. 이런 상황에서는, 네임스페이스 충돌이 가끔 일어납니다. 이런 일이 발생한다면, 플러그인에 `.noConflict` 메서드를 이용하여 변수로 반환 받을 수 있습니다.  

{% highlight js %}
var bootstrapButton = $.fn.button.noConflict() // 앞에 할당된 변수에 $.fn.button 을 반환합니다
$.fn.bootstrapBtn = bootstrapButton            // $().bootstrapBtn 에 부트스트랩 기능을 부여합니다
{% endhighlight %}

## 버전 숫자

부트스트랩의 jQuery 플러그인의 버전은 플러그인 생성자의 `VERSION` 속성을 통해 접근할 수 있습니다. 툴팁 플러그인의 경우, 예를 들면,

{% highlight js %}
$.fn.tooltip.Constructor.VERSION // => "{{ site.current_version }}"
{% endhighlight %}

## 자바스크립트가 비활성화되었을 때 특별한 대비책은 없습니다

부트스트랩 플러그인은 자바스크립트가 비활성화되었을 때를 특별히 대비하지 않습니다. 만약 당신이 이런 경우의 사용자 경험을 보완하려면, 사용자들에게 상황을 설명하기 위해 [`<noscript>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/noscript) 를 사용하거나 당신만의 대비책을 추가하세요.

{% capture callout %}
##### 서드파티 라이브러리

**부트스트랩은 공식적으로 Prototype 나 jQuery UI 같은 서드파티 자바스크립트 라이브러리를 지원하지 않습니다** `.noConflict` 와 네임스페이스 이벤트에도 불구하고, 혼자 고쳐야만 하는 호환성 문제가 있을 수 있습니다.
 
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## Util

모든 부트스트랩 자바스크립트 파일은 `util.js` 에 의존하며 다른 자바스크립트 파일과 함께 포함되어야 합니다. 만약 컴파일된 (혹은 압축된) `bootstrap.js` 을 사용한다면, 그것이 이미 들어있기 때문에 포함할 필요가 없습니다.

`util.js` 는 CSS 전환 에뮬레이터뿐만 아니라 유틸리티 함수들과 `transitionEnd` 이벤트를 위한 기본 헬퍼를 포함합니다. 그것은 다른 플러그인이 CSS 전환 지원을 확인하고 완료되지 않은 전환을 잡아내는데 사용됩니다.
