---
layout: docs
title: 알림
description: 유연한 알림 메시지를 통해 일반적인 사용자 동작을 위해 상황별 피드백 메시지를 제공합니다.
group: components
toc: true
---

## 예제

알림은 어떤 길이도 가능하며, 닫기 버튼도 사용할 수 있습니다. 올바른 스타일을 적용하기 위해서, 8가지 상황별 클래스 (예: `.alert-success`) 중 하나를 필수로 사용해야 합니다. 인라인 닫기를 위해, [알림 jQuery 플러그인](#닫기) 을 사용하세요.  

{% capture example %}
{% for color in site.data.theme-colors %}
<div class="alert alert-{{ color.name }}" role="alert">
  간단한 {{ color.name }} 알림입니다. 확인해보세요!
</div>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

{% include callout-warning-color-assistive-technologies.md %}

### 링크 색상

`.alert-link` 유틸리티 클래스를 사용하여 알림에 어울리는 색상을 빠르게 제공하세요.

{% capture example %}
{% for color in site.data.theme-colors %}
<div class="alert alert-{{ color.name }}" role="alert">
  <a href="#" class="alert-link">예제 링크</a> 를 포함한 {{ color.name }} 알림 예제입니다. 원한다면 클릭해보세요.
</div>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

### 추가 콘텐츠

또한 알림은 제목, 단락, 구분선 같은 부가적인 HTML 요소를 포함할 수 있습니다.

{% capture example %}
<div class="alert alert-success" role="alert">
  <h4 class="alert-heading">Well done!</h4>
  <p>Aww yeah, you successfully read this important alert message. This example text is going to run a bit longer so that you can see how spacing within an alert works with this kind of content.</p>
  <hr>
  <p class="mb-0">Whenever you need to, be sure to use margin utilities to keep things nice and tidy.</p>
</div>
{% endcapture %}
{% include example.html content=example %}


### 닫기

알림 자바스크립트 플러그인을 사용하면 알림을 닫을 수 있습니다. 방법은 다음과 같습니다.

- 알림 플러그인 아니면 컴파일된 부트스트랩 자바스크립트를 로드했는지 확인하세요.
- 소스에서 자바스크립트를 빌드하는 경우는 [`util.js` 가 필요합니다]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/javascript/#util). 컴파일된 버전은 이것을 포함합니다. 
- 닫기 버튼과 `.alert-dismissible` 클래스를 추가합니다. 이 클래스는 알림의 오른쪽에 여분의 패딩을 추가하고 `.close` 버튼의 위치를 지정합니다.
- 닫기 버튼에서, `data-dismiss="alert"` 속성을 추가하세요. 이 속성은 자바스크립트 기능성이 트리거 됩니다. 모든 장치에서 올바른 동작을 위해 `<button>` 요소와 함께 사용하세요.
- 알림을 닫을 때 애니메이션을 적용하려면, `.fade` 와 `.show` 클래스를 추가해야 합니다.

라이브 데모에서 실제로 이것을 볼 수 있습니다.

{% capture example %}
<div class="alert alert-warning alert-dismissible fade show" role="alert">
  <strong>Holy guacamole!</strong> You should check in on some of those fields below.
  <button type="button" class="close" data-dismiss="alert" aria-label="Close">
    <span aria-hidden="true">&times;</span>
  </button>
</div>
{% endcapture %}
{% include example.html content=example %}

## 자바스크립트 동작

### 트리거

자바스크립트를 통해 알림을 닫을 수 있습니다.

{% highlight js %}
$('.alert').alert()
{% endhighlight %}

아니면 **알림 내의** 버튼에 `data` 속성을 사용하여 다음과 같이 구현할 수 있습니다.

{% highlight html %}
<button type="button" class="close" data-dismiss="alert" aria-label="Close">
  <span aria-hidden="true">&times;</span>
</button>
{% endhighlight %}

알림을 닫으면 그것은 DOM 에서 제거 됩니다.

### 메서드

| 메서드 | 설명 |
| --- | --- |
| `$().alert()` | `data-dismiss="alert"` 속성이 있는 하위 요소에 대한 클릭 이벤트를 수신합니다. (data-api 의 자동 초기화를 사용할 때는 필요 없음) |
| `$().alert('close')` | 알림을 DOM 에서 제거하여 닫습니다. 만약 요소에 `.fade` 와 `.show` 클래스가 있으면, 알림은 제거되기 전에 서서히 사라집니다. |
| `$().alert('dispose')` | 요소의 알림을 소멸합니다. |

{% highlight js %}$(".alert").alert('close'){% endhighlight %}

### 이벤트

부트스트랩의 알림 플러그인은 알림 기능에 연결하기 위한 몇가지 이벤트를 노출합니다.

| 이벤트 | 설명 |
| --- | --- |
| `close.bs.alert` | 이 이벤트는 <code>close</code> 메서드가 호출될 때 즉시 발생합니다. |
| `closed.bs.alert` | 이 이벤트는 알림이 닫히게 되면 발생합니다. (CSS 전환이 완료될 때 까지 대기할 것입니다). |

{% highlight js %}
$('#myAlert').on('closed.bs.alert', function () {
  // do something…
})
{% endhighlight %}
