---
layout: docs
title: 버튼 그룹
description: 버튼 그룹으로 한줄에 일련의 버튼을 그룹화하고, 자바스크립트로 슈퍼 파워를 부여합니다.
group: components
toc: true
---

## 기본 예제

`.btn` 이 있는 일련의 버튼을 `.btn-group` 으로 감싸세요. [버튼 플러그인]({{ site.baseurl }}/docs/{{ site.docs_version }}/components/buttons/#button-plugin) 으로 자바스크립트 라디오 및 체크박스 스타일 동작을 선택적으로 추가할 수 있습니다. 

{% capture example %}
<div class="btn-group" role="group" aria-label="Basic example">
  <button type="button" class="btn btn-secondary">Left</button>
  <button type="button" class="btn btn-secondary">Middle</button>
  <button type="button" class="btn btn-secondary">Right</button>
</div>
{% endcapture %}
{% include example.html content=example %}

{% capture callout %}
##### 올바른 `role` 를 보장하고 레이블을 제공하세요

그룹화된 일련의 버튼을 (스크린 리더 같은) 보조 기술에 전달하기 위해서는 적절한 `role` 특성을 제공해야 합니다. 버튼 그룹을 위해서는 `role="group"` 이어야 하고, 툴바는 `role="toolbar"` 이어야 합니다.

또한, 버튼 그룹과 툴바는 올바른 역할 특성이 있음에도 불구하고 대부분의 보조 기술이 이를 알리지 않으므로 명시적인 레이블이 주어져야 합니다. 제공되는 예제에서는 `aria-label` 을 사용하지만 `aria-labelledby` 같은 것도 또한 사용될 수 있습니다. 
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## 버튼 툴바

버튼 그룹 세트들을 버튼 툴바로 결합하여 보다 복잡한 컴포넌트를 만듭니다. 버튼 그룹, 버튼 등의 간격 조정하는 것은 유틸리티 클래스를 사용하세요. 

{% capture example %}
<div class="btn-toolbar" role="toolbar" aria-label="Toolbar with button groups">
  <div class="btn-group mr-2" role="group" aria-label="First group">
    <button type="button" class="btn btn-secondary">1</button>
    <button type="button" class="btn btn-secondary">2</button>
    <button type="button" class="btn btn-secondary">3</button>
    <button type="button" class="btn btn-secondary">4</button>
  </div>
  <div class="btn-group mr-2" role="group" aria-label="Second group">
    <button type="button" class="btn btn-secondary">5</button>
    <button type="button" class="btn btn-secondary">6</button>
    <button type="button" class="btn btn-secondary">7</button>
  </div>
  <div class="btn-group" role="group" aria-label="Third group">
    <button type="button" class="btn btn-secondary">8</button>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

툴바 내 버튼 그룹을 입력 그룹과 합께 자유롭게 조합하세요. 위 예제와 마찬가지로, 간격 조정에는 유틸리티 클래스가 필요할 것입니다.

{% capture example %}
<div class="btn-toolbar mb-3" role="toolbar" aria-label="Toolbar with button groups">
  <div class="btn-group mr-2" role="group" aria-label="First group">
    <button type="button" class="btn btn-secondary">1</button>
    <button type="button" class="btn btn-secondary">2</button>
    <button type="button" class="btn btn-secondary">3</button>
    <button type="button" class="btn btn-secondary">4</button>
  </div>
  <div class="input-group">
    <div class="input-group-prepend">
      <div class="input-group-text" id="btnGroupAddon">@</div>
    </div>
    <input type="text" class="form-control" placeholder="Input group example" aria-label="Input group example" aria-describedby="btnGroupAddon">
  </div>
</div>

<div class="btn-toolbar justify-content-between" role="toolbar" aria-label="Toolbar with button groups">
  <div class="btn-group" role="group" aria-label="First group">
    <button type="button" class="btn btn-secondary">1</button>
    <button type="button" class="btn btn-secondary">2</button>
    <button type="button" class="btn btn-secondary">3</button>
    <button type="button" class="btn btn-secondary">4</button>
  </div>
  <div class="input-group">
    <div class="input-group-prepend">
      <div class="input-group-text" id="btnGroupAddon2">@</div>
    </div>
    <input type="text" class="form-control" placeholder="Input group example" aria-label="Input group example" aria-describedby="btnGroupAddon2">
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

## 크기 조정

여러 버튼 그룹을 가질때, 그룹 내 모든 버튼에 크기 조정 클래스를 적용하는 대신, 그냥 `.btn-group` 에 `.btn-group-*` 를 추가하시면 됩니다.

<div class="bd-example">
  <div class="btn-group btn-group-lg" role="group" aria-label="Large button group">
    <button type="button" class="btn btn-secondary">Left</button>
    <button type="button" class="btn btn-secondary">Middle</button>
    <button type="button" class="btn btn-secondary">Right</button>
  </div>
  <br>
  <div class="btn-group" role="group" aria-label="Default button group">
    <button type="button" class="btn btn-secondary">Left</button>
    <button type="button" class="btn btn-secondary">Middle</button>
    <button type="button" class="btn btn-secondary">Right</button>
  </div>
  <br>
  <div class="btn-group btn-group-sm" role="group" aria-label="Small button group">
    <button type="button" class="btn btn-secondary">Left</button>
    <button type="button" class="btn btn-secondary">Middle</button>
    <button type="button" class="btn btn-secondary">Right</button>
  </div>
</div>

{% highlight html %}
<div class="btn-group btn-group-lg" role="group" aria-label="...">...</div>
<div class="btn-group" role="group" aria-label="...">...</div>
<div class="btn-group btn-group-sm" role="group" aria-label="...">...</div>
{% endhighlight %}

## 중첩

드롭다운 메뉴를 일련의 버튼들과 함께 사용하려면 `.btn-group` 안에 `.btn-group` 를 배치하세요.

{% capture example %}
<div class="btn-group" role="group" aria-label="Button group with nested dropdown">
  <button type="button" class="btn btn-secondary">1</button>
  <button type="button" class="btn btn-secondary">2</button>

  <div class="btn-group" role="group">
    <button id="btnGroupDrop1" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
      Dropdown
    </button>
    <div class="dropdown-menu" aria-labelledby="btnGroupDrop1">
      <a class="dropdown-item" href="#">Dropdown link</a>
      <a class="dropdown-item" href="#">Dropdown link</a>
    </div>
  </div>
</div>
{% endcapture %}
{% include example.html content=example %}

## 수직형

버튼들을 수평이 아닌 수직으로 나타나게 합니다. **분할 버튼 드롭다운은 지원되지 않습니다.**

<div class="bd-example">
  <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
  </div>
</div>


<div class="bd-example">
  <div class="btn-group-vertical" role="group" aria-label="Vertical button group">
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
    <div class="btn-group" role="group">
      <button id="btnGroupVerticalDrop1" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        Dropdown
      </button>
      <div class="dropdown-menu" aria-labelledby="btnGroupVerticalDrop1">
        <a class="dropdown-item" href="#">Dropdown link</a>
        <a class="dropdown-item" href="#">Dropdown link</a>
      </div>
    </div>
    <button type="button" class="btn btn-secondary">Button</button>
    <button type="button" class="btn btn-secondary">Button</button>
    <div class="btn-group" role="group">
      <button id="btnGroupVerticalDrop2" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        Dropdown
      </button>
      <div class="dropdown-menu" aria-labelledby="btnGroupVerticalDrop2">
        <a class="dropdown-item" href="#">Dropdown link</a>
        <a class="dropdown-item" href="#">Dropdown link</a>
      </div>
    </div>
    <div class="btn-group" role="group">
      <button id="btnGroupVerticalDrop3" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        Dropdown
      </button>
      <div class="dropdown-menu" aria-labelledby="btnGroupVerticalDrop3">
        <a class="dropdown-item" href="#">Dropdown link</a>
        <a class="dropdown-item" href="#">Dropdown link</a>
      </div>
    </div>
    <div class="btn-group" role="group">
      <button id="btnGroupVerticalDrop4" type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        Dropdown
      </button>
      <div class="dropdown-menu" aria-labelledby="btnGroupVerticalDrop4">
        <a class="dropdown-item" href="#">Dropdown link</a>
        <a class="dropdown-item" href="#">Dropdown link</a>
      </div>
    </div>
  </div>
</div>

{% highlight html %}
<div class="btn-group-vertical">
  ...
</div>
{% endhighlight %}
