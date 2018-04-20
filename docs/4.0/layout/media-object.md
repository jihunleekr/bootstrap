---
layout: docs
title: 미디어 개체 
description: 부트스트랩의 미디어 개체에 대한 문서 및 예제는 블로그 댓글, 트윗, 좋아요 등과 같은 반복적인 컴포넌트를 구성합니다.
group: layout
toc: true
---

## 예제

[미디어 개체](http://www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code/) 는 복잡하고 반복적인 컴포넌트를 만드는 것을 돕습니다. 이 컴포넌트는 내용이 미디어를 둘러싸지 않고 나란히 위치합니다. 또한, flexbox 도움으로 두가지 필수 클래스만으로 이것을 수행을 할 수 있습니다.

다음은 단일 미디어 개체의 예입니다. 콘텐츠 주위를 감싸는 `.media` 와 `.media-body` 등 두 클래스만 요구됩니다. 추가적인 패딩과 여백은 [spacing 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/spacing/) 를 통해 조정할 수 있습니다.

{% capture example %}
<div class="media">
  <img class="mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
  <div class="media-body">
    <h5 class="mt-0">미디어 제목</h5>
    Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

{% capture callout %}
##### Flexbug #12: 인라인 요소는 flex 항목으로 다뤄지지 않습니다.

인터넷 익스플로러 10-11 은 좋아요나 이미지같은 인라인 요소들을 flex 항목으로 렌더링하지 않습니다. 유일한 차선책은 인라인이 아닌 `display` 값 (예: `block`, `inline-block`, `flex`) 을 설정하는 것입니다. 우리는 간편하게 [display 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/display/) 중 하나인 `.d-flex` 를 사용할 것을 제안합니다.

**출처:** [Flexbug 들 - 깃허브](https://github.com/philipwalton/flexbugs#12-inline-elements-are-not-treated-as-flex-items)
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## 중첩

미디어 개체는 무한대로 중첩될 수 있습니다만, 적당한 선에서 사용하길 권장합니다. 상위 미디어 개체의 `.media-body` 내에 중첩할 `.media` 를 배치하세요.

{% capture example %}
<div class="media">
  <img class="mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
  <div class="media-body">
    <h5 class="mt-0">미디어 제목</h5>
    Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.

    <div class="media mt-3">
      <a class="pr-3" href="#">
        <img data-src="holder.js/64x64" alt="Generic placeholder image">
      </a>
      <div class="media-body">
        <h5 class="mt-0">미디어 제목</h5>
        Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
      </div>
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

## 정렬

미디어 개체 내 미디어는 flexbox 유틸리티를 이용해서 `.media-body` 내용의 상단(기본값), 중단, 하단에 정렬할 수 있습니다.

{% capture example %}
<div class="media">
  <img class="align-self-start mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
  <div class="media-body">
    <h5 class="mt-0">상단 정렬된 미디어</h5>
    <p>Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.</p>
    <p>Donec sed odio dui. Nullam quis risus eget urna mollis ornare vel eu leo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.</p>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

{% capture example %}
<div class="media">
  <img class="align-self-center mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
  <div class="media-body">
    <h5 class="mt-0">중단 정렬된 미디어</h5>
    <p>Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.</p>
    <p class="mb-0">Donec sed odio dui. Nullam quis risus eget urna mollis ornare vel eu leo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.</p>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

{% capture example %}
<div class="media">
  <img class="align-self-end mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
  <div class="media-body">
    <h5 class="mt-0">하단 정렬된 미디어</h5>
    <p>Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.</p>
    <p class="mb-0">Donec sed odio dui. Nullam quis risus eget urna mollis ornare vel eu leo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.</p>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

## 순서

HTML 을 수정하거나 맞춤 flexbox CSS 를 추가하여 `order` 속성을 설정해서 미디어 개체 내 콘텐츠의 순서를 변경하세요.

{% capture example %}
<div class="media">
  <div class="media-body">
    <h5 class="mt-0 mb-1">미디어 개체</h5>
    Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
  </div>
  <img class="ml-3" data-src="holder.js/64x64" alt="Generic placeholder image">
</div>
{% endcapture %}
{% include example.html content=example %}

## 미디어 목록

미디어 개체는 구조적인 요구사항이 거의 없기때문에, 이 클래스들을 목록 HTML 요소에 사용할 수도 있습니다. `<ul>` 이나 `<ol>` 에, `.list-unstyled` 를 추가하여 브라우저 기본 목록 스타일을 제거하고, `<li>` 에 `.media` 를 적용합니다. 늘 그렇듯이, 미세한 조정이 필요한 곳에는 spacing 유틸리티를 사용하세요.

{% capture example %}
<ul class="list-unstyled">
  <li class="media">
    <img class="mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">목록 기반 미디어 개체</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
  <li class="media my-4">
    <img class="mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">목록 기반 미디어 개체</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
  <li class="media">
    <img class="mr-3" data-src="holder.js/64x64" alt="Generic placeholder image">
    <div class="media-body">
      <h5 class="mt-0 mb-1">목록 기반 미디어 개체</h5>
      Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis. Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis in faucibus.
    </div>
  </li>
</ul>
{% endcapture %}
{% include example.html content=example %}
