---
layout: docs
title: 이미지
description: 반응형 동작에 이미지를 맞추고 (부모요소 보다 커지지 않도록) 클래스로 이미지에 가벼운 스타일을 추가하기 위한 설명서와 예제
group: content
toc: true
---

## 반응형 이미지

부트스트랩 내의 이미지는 `.img-fluid` 으로 반응형으로 만들어집니다. `max-width: 100%;` 와 `height: auto;` 는 이미지에 적용되어 부모 요소에 크기를 맞추게 됩니다.

<div class="bd-example">
  <img data-src="holder.js/100px250" class="img-fluid" alt="Generic responsive image">
</div>

{% highlight html %}
<img src="..." class="img-fluid" alt="Responsive image">
{% endhighlight %}

{% capture callout %}
##### SVG 이미지와 IE 10

인터넷 익스플로러 10 에서 `.img-fluid` 가 들어간 SVG 이미지는 불균형하게 크기가 지정됩니다. 이걸 고치려면 필요한 곳에 `width: 100% \9;` 을 추가하세요. 이 코드는 다른 이미지 포멧의 크기를 잘못 지정하므로 부트스트랩이 자동으로 적용하지 않습니다.
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## 이미지 썸네일

[둥근 테두리 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/borders/) 뿐만 아니라, `.img-thumbnail` 를 사용하여 이미지에 둥근 1px 테두리 모양을 부여할 수 있습니다.

<div class="bd-example bd-example-images">
  <img data-src="holder.js/200x200" class="img-thumbnail" alt="A generic square placeholder image with a white border around it, making it resemble a photograph taken with an old instant camera">
</div>

{% highlight html %}
<img src="..." alt="..." class="img-thumbnail">
{% endhighlight %}

## 이미지 정렬

이미지를 [float 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/float) 또는 [텍스트 정렬 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/text/#text-alignment) 로 정렬하세요. `block` 류의 이미지는 [`.mx-auto` 여백 유틸리티 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/spacing/#horizontal-centering) 을 사용하여 중앙에 배치할 수 있습니다.  

<div class="bd-example bd-example-images">
  <img data-src="holder.js/200x200" class="rounded float-left" alt="A generic square placeholder image with rounded corners">
  <img data-src="holder.js/200x200" class="rounded float-right" alt="A generic square placeholder image with rounded corners">
</div>

{% highlight html %}
<img src="..." class="rounded float-left" alt="...">
<img src="..." class="rounded float-right" alt="...">
{% endhighlight %}

<div class="bd-example bd-example-images">
  <img data-src="holder.js/200x200" class="rounded mx-auto d-block" alt="A generic square placeholder image with rounded corners">
</div>

{% highlight html %}
<img src="..." class="rounded mx-auto d-block" alt="...">
{% endhighlight %}

<div class="bd-example bd-example-images">
  <div class="text-center">
    <img data-src="holder.js/200x200" class="rounded" alt="A generic square placeholder image with rounded corners">
  </div>
</div>

{% highlight html %}
<div class="text-center">
  <img src="..." class="rounded" alt="...">
</div>
{% endhighlight %}


## Picture

특정 `<img>` 에 대해 여러 `<source>` 요소를 지정하기 위해 `<picture>` 를 사용한다면, `.img-*` 클래스를 `<picture>` 가 아닌 `<img>` 에 추가해야함을 명심하세요. 

{% highlight html %}
​<picture>
  <source srcset="..." type="image/svg+xml">
  <img src="..." class="img-fluid img-thumbnail" alt="...">
</picture>
{% endhighlight %}
