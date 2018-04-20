---
layout: docs
title: 버튼
description: 폼, 대화상자 등에서 작업을 위해 다양한 크기, 상태 등을 지원하는 부트스트랩의 맞춤 버튼을 사용해보세요.
group: components
redirect_from: "/docs/4.0/components/"
toc: true
---

## 예제

부트스트랩은 몇가지 미리 정의된 버튼 스타일을 포함합니다. 각 스타일은 의미 체계적 목적을 제공하며 더 많은 제어를 위해 몇가지 추가 기능이 있습니다.

{% capture example %}
{% for color in site.data.theme-colors %}
<button type="button" class="btn btn-{{ color.name }}">{{ color.name | capitalize }}</button>{% endfor %}

<button type="button" class="btn btn-link">Link</button>
{% endcapture %}
{% include example.html content=example %}

{% include callout-warning-color-assistive-technologies.md %}

## 버튼 태그

`.btn` 클래스는 `<button>` 요소에 사용되도록 설계되었습니다. 하지만, `<a>` 나 `<input>` 요소에도 사용할 수 있습니다 (일부 브라우저는 약간 다른 렌더링을 적용할 수도 있습니다).

현재 페이지에서 새로운 페이지나 섹션으로 연결되는 것이 아니라 페이지 내에서 기능 (접히는 콘텐츠같은) 에 사용되는 `<a>` 요소에 버튼 클래스를 사용할때는, 스크린 리더같은 보조 기술에 목적을 적절하게 전달하기 위해 `role="button"` 를 제공해야 합니다.

{% capture example %}
<a class="btn btn-primary" href="#" role="button">Link</a>
<button class="btn btn-primary" type="submit">Button</button>
<input class="btn btn-primary" type="button" value="Input">
<input class="btn btn-primary" type="submit" value="Submit">
<input class="btn btn-primary" type="reset" value="Reset">
{% endcapture %}
{% include example.html content=example %}

## 외곽선 버튼

무거운 배경색이 아닌 버튼이 필요하세요? 기본 수식 클래스를 `.btn-outline-*` 로 교체하여 모든 배경 이미지와 색상을 버튼에서 제거하세요.

{% capture example %}
{% for color in site.data.theme-colors %}
<button type="button" class="btn btn-outline-{{ color.name }}">{{ color.name | capitalize }}</button>{% endfor %}
{% endcapture %}
{% include example.html content=example %}

## 크기

더 크거나 작은 버튼을 원하세요? 크기 조정을 위해 `.btn-lg` 혹은 `.btn-sm` 를 추가하세요.

{% capture example %}
<button type="button" class="btn btn-primary btn-lg">큰 버튼</button>
<button type="button" class="btn btn-secondary btn-lg">큰 버튼</button>
{% endcapture %}
{% include example.html content=example %}

{% capture example %}
<button type="button" class="btn btn-primary btn-sm">작은 버튼</button>
<button type="button" class="btn btn-secondary btn-sm">작은 버튼</button>
{% endcapture %}
{% include example.html content=example %}

`.btn-block` 을 추가하여 부모 요소의 최대너비에 걸쳐 있는 블록 레벨 버튼을 만드세요.

{% capture example %}
<button type="button" class="btn btn-primary btn-lg btn-block">Block level button</button>
<button type="button" class="btn btn-secondary btn-lg btn-block">Block level button</button>
{% endcapture %}
{% include example.html content=example %}

## 활성 상태

버튼은 활성화되면 눌린 것처럼 (어두운 배경, 어두운 테두리, 오목한 그림자로) 보여집니다. **가상클래스를 사용하기 때문에 `<button>` 에 클래스를 추가할 필요는 없습니다**. 하지만, 프로그래밍 방식으로 상태를 모사할 필요가 있다면 `.active` 를 사용하여 (그리고  <code>aria-pressed="true"</code> 속성을 포함하여) 같은 모습을 적용할 수 있습니다.

{% capture example %}
<a href="#" class="btn btn-primary btn-lg active" role="button" aria-pressed="true">Primary link</a>
<a href="#" class="btn btn-secondary btn-lg active" role="button" aria-pressed="true">Link</a>
{% endcapture %}
{% include example.html content=example %}

## 비활성 상태

`<button>` 요소에 `disabled` 속성을 추가하여 비활성 상태로 보여지게 합니다.

{% capture example %}
<button type="button" class="btn btn-lg btn-primary" disabled>Primary button</button>
<button type="button" class="btn btn-secondary btn-lg" disabled>Button</button>
{% endcapture %}
{% include example.html content=example %}

`<a>` 요소를 사용하는 비활성 버튼은 조금 다르게 동작합니다.

- `<a>` 는 `disabled` 속성을 지원하지 않으므로 비활성화 된 것으로 보이게 하려면 `.disabled` 클래스를 추가해야 합니다. 
- 앵커 버튼의 모든 `pointer-events` 를 비활성화 하기 위해 일부 미래지향적인 스타일이 포함되어 있습니다. 해당 속성을 지원하는 브라우저에서는 비활성화된 커서가 전혀 표시되지 않습니다. 
- 비활성화된 버튼은 `aria-disabled="true"` 속성을 포함해서 보조 기술에게 요소의 상태를 알려주어야 합니다.

{% capture example %}
<a href="#" class="btn btn-primary btn-lg disabled" tabindex="-1" role="button" aria-disabled="true">Primary link</a>
<a href="#" class="btn btn-secondary btn-lg disabled" tabindex="-1" role="button" aria-disabled="true">Link</a>
{% endcapture %}
{% include example.html content=example %}

{% capture callout %}
##### 링크 기능성 경고

`.disabled` 클래스는 링크의 기능성을 비활성화하기 위해 `pointer-events: none` 를 사용합니다만, 이러한 CSS 속성은 아직 표준화 되지 않았습니다. 게다가, `pointer-events: none` 를 지원하는 브라우저에서도 키보드 탐색은 영향을 받지 않습니다. 이는 키보드 사용자와 보조 기술 사용자는 여전히 이 링크들을 활성화할 수 있다는 의미입니다. 따라서 안전을 위해 링크에 `tabindex="-1"` 특성을 추가하고 기능성을 비활성화 하기 위한 맞춤 자바스크립트를 사용하세요.
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## 버튼 플러그인

버튼으로 더 많은 작업을 수행하세요. 버튼 상태를 컨트롤 하거나 툴바 컴포넌트 같은 버튼 그룹을 만들어보세요.

### 토글 상태

`data-toggle="button"` 를 추가하여 버튼의 `active` 상태를 토글하세요. 만약 미리 버튼을 토글하려면, `<button>` 에 `.active` 클래스 **와** `aria-pressed="true"` 를 수동으로 추가해야 합니다.

{% capture example %}
<button type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">
  Single toggle
</button>
{% endcapture %}
{% include example.html content=example %}

### 체크박스와 라디오 버튼

부트스트랩의 `.button` 스타일은 `<label>` 과 같은 다른 요소에 적용되어 버튼 스타일 체크박스나 라디오에 토글링을 제공합니다. 수정된 버튼들을 포함한 `.btn-group` 에 `data-toggle="buttons"` 을 추가하여 자바스크립트를 통해 토글링 동작이 활성화 되도록 하고 `.btn-group-toggle` 를 추가하여 `<input>` 들에 스타일을 적용하세요. **버튼 모습의 단일 input 이나 그룹을 만들 수 있습니다.** 

이 버튼들의 체크된 상태는 버튼의 **오직 `click` 이벤트를 통해서만 업데이트 됩니다.** 만약 input 을 업데이트하기 위해 `<input type="reset">` 을 사용하거나 input 의 `checked` 속성을 수동으로 적용하는 것과 같이 다른 방법을 사용하려면 `<label>` 의 `.active` 를 수동으로 토글하는 것이 필요할 것입니다.

미리 체크된 버튼은 input 의 `<label>` 에 `.active` 클래스를 수동으로 추가하는 것이 필요합니다.

{% capture example %}
<div class="btn-group-toggle" data-toggle="buttons">
  <label class="btn btn-secondary active">
    <input type="checkbox" checked autocomplete="off"> Checked
  </label>
</div>
{% endcapture %}
{% include example.html content=example %}

{% capture example %}
<div class="btn-group btn-group-toggle" data-toggle="buttons">
  <label class="btn btn-secondary active">
    <input type="radio" name="options" id="option1" autocomplete="off" checked> Active
  </label>
  <label class="btn btn-secondary">
    <input type="radio" name="options" id="option2" autocomplete="off"> Radio
  </label>
  <label class="btn btn-secondary">
    <input type="radio" name="options" id="option3" autocomplete="off"> Radio
  </label>
</div>
{% endcapture %}
{% include example.html content=example %}

### 메서드

| 메서드 | 설명 |
| --- | --- |
| `$().button('toggle')` | 눌림 상태를 토글합니다. 버튼에 활성화 된 모양을 부여합니다. |
| `$().button('dispose')` | 요소의 버튼을 소멸합니다. |
