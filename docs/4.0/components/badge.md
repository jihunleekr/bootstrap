---
layout: docs
title: 배지
description: 작은 카운터와 레이블 컴포넌트인 배지에 대한 설명서와 예제
group: components
toc: true
---

## 예제

배지는 상대적인 글꼴 크기와 `em` 단위를 사용하여 직계 부모 요소의 크기에 따라 크기를 맞춥니다.

<div class="bd-example">
<div class="h1">Example heading <span class="badge badge-secondary">New</span></div>
<div class="h2">Example heading <span class="badge badge-secondary">New</span></div>
<div class="h3">Example heading <span class="badge badge-secondary">New</span></div>
<div class="h4">Example heading <span class="badge badge-secondary">New</span></div>
<div class="h5">Example heading <span class="badge badge-secondary">New</span></div>
<div class="h6">Example heading <span class="badge badge-secondary">New</span></div>
</div>

{% highlight html %}
<h1>Example heading <span class="badge badge-secondary">New</span></h1>
<h2>Example heading <span class="badge badge-secondary">New</span></h2>
<h3>Example heading <span class="badge badge-secondary">New</span></h3>
<h4>Example heading <span class="badge badge-secondary">New</span></h4>
<h5>Example heading <span class="badge badge-secondary">New</span></h5>
<h6>Example heading <span class="badge badge-secondary">New</span></h6>
{% endhighlight %}

배지는 카운터를 제공하기 위해 링크나 버튼의 일부로 사용될 수 있습니다.

{% capture example %}
<button type="button" class="btn btn-primary">
  알림 <span class="badge badge-light">4</span>
</button>
{% endcapture %}
{% include example.html content=example %}

사용 방법에 따라 배지는 스크린 리더 및 유사한 보조 기술의 사용자들에게 혼동을 줄 수 있습니다. 배지의 스타일은 목적에 관해서 시각적인 단서를 제공하지만, 이 사용자들에게 배지의 내용은 간단하게 표현됩니다. 상황에 따라, 이 배지는 문장, 링크, 버튼의 끝에 있는 아무 의미없는 단어나 숫자처럼 보일 수 있습니다.

컨텍스트가 분명 ("알림" 에서 "4" 는 알림의 수라고 이해됨) 하지 않으면, 시각적으로 숨겨진 텍스트로 추가적인 컨텍스트를 포함하는 것을 고려해보세요.  

{% capture example %}
<button type="button" class="btn btn-primary">
  프로필 <span class="badge badge-light">9</span>
  <span class="sr-only">읽지 않은 메시지</span>
</button>
{% endcapture %}
{% include example.html content=example %}

## 상황별 변형

배지의 모습을 바꾸려면 아래 나오는 수식 클래스 중 하나를 추가하세요.

{% capture example %}
{% for color in site.data.theme-colors %}
<span class="badge badge-{{ color.name }}">{{ color.name | capitalize }}</span>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

{% include callout-warning-color-assistive-technologies.md %}

## 알약형 배지

`.badge-pill` 수식 클래스를 사용하여 배지를 좀 더 둥글게 만듭니다 (더 큰 `border-radius` 와 수평적인 추가 `padding` 으로). v3 의 배지를 찾으신다면 유용할 것입니다.

{% capture example %}
{% for color in site.data.theme-colors %}
<span class="badge badge-pill badge-{{ color.name }}">{{ color.name | capitalize }}</span>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

## 링크

`<a>` 요소에 상황별 `.badge-*` 클래스를 이용하여, 커서를 올렸을 때와 포커스 상태에 대해 동작하는 배지를 간편하게 제공할 수 있습니다.

{% capture example %}
{% for color in site.data.theme-colors %}
<a href="#" class="badge badge-{{ color.name }}">{{ color.name | capitalize }}</a>{% endfor %}
{% endcapture %}
{% include example.html content=example %}
