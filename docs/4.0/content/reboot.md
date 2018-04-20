---
layout: docs
title: Reboot
description: 하나의 파일에서 요소별 CSS 변경사항 모음인 Reboot 는 우아하고 일관되며 간단한 기준을 제공합니다.
group: content
redirect_from: "/docs/4.0/content/"
toc: true
---

## 접근

Normalize 기반으로 만들어진 Reboot 는 요소 선택자만을 사용하여 다소 독창적인 스타일의 많은 HTML 요소들을 제공합니다. 추가적인 스타일은 클래스로 작동됩니다. 예를 들면, 우리는 `<table>` 에 간단한 기준점을 만들고 그 다음 `.table`, `.table-bordered` 등을 제공합니다.   

Reboot 에서 오버라이드할 항목을 선택하는 것에 대한 지침과 이유는 다음과 같습니다.

- 확장가능한 컴포넌트 간격에 `em` 대신 `rem` 을 사용하도록 일부 브라우저 기본값을 업데이트 합니다.
- `margin-top` 을 피합니다. 수직 여백은 겹쳐져 예상치 못한 결과를 초래할 수 있습니다. 더 중요한 것은, `margin` 을 단방향으로 해야 생각하기에 간단해집니다.
- 장치 크기에 따라 쉽게 조정할 수 있도록 block 요소는 `margin` 을 위해 `rem` 을 사용해야 합니다.
- `font` 관련 속성은 가능한 `inherit` 을 사용하여 선언을 최소화하세요.

## 페이지 기본값

`<html>` 와 `<body>` 요소는 더 나은 page-wide 기본값을 제공하도록 업데이트 되었습니다. 좀 더 구체적으로:

- `box-sizing` 은 `*::before` 과 `*::after` 을 포함하여 모든 요소에 전역적으로 `border-box` 으로 설정됩니다. 이렇게 하면 요소의 선언된 너비는 절대 패딩이나 테두리로 인해 넘치지 않습니다.
  - `font-size` 는 `<html>` 에 선언되어 있지 않지만, `16px` 라고 가정합니다 (브라우저 기본값). `<body>` 에는 사용자 환경설정을 존중하고 더 나은 접근성을 보장하면서 미디어 쿼리를 통해 쉬운 반응형 글꼴 크기 조정을 위해 `font-size: 1rem` 가 적용됩니다.
- `<body>` 는 또한 전역 `font-family`, `line-height`, `text-align` 을 설정합니다. 이것은 글꼴 불일치를 막기 위해 나중에 일부 폼 요소들에 의해 상속됩니다.
- 안전을 위해, `<body>` 는 `background-color` 을 선언했으며, 기본값은 `#fff` 입니다.

## 기본 글꼴 스택

기본 웹 글꼴 (Helvetica Neue, Helvetica, Arial) 은 부트스트랩에 누락되었으며 모든 장치 및 OS 에서 최적의 텍스트 렌더링을 위해 "기본 글꼴 스택" 으로 교체됩니다.

The default web fonts (Helvetica Neue, Helvetica, and Arial) have been dropped in Bootstrap 4 and replaced with a "native font stack" for optimum text rendering on every device and OS. 
[*Smashing Magazine* 기사에서 기본 글꼴 스택](https://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/) 에 관해서 더 읽어보세요.

{% highlight sass %}
$font-family-sans-serif:
  // Safari for OS X and iOS (San Francisco)
  -apple-system,
  // Chrome < 56 for OS X (San Francisco)
  BlinkMacSystemFont,
  // Windows
  "Segoe UI",
  // Android
  "Roboto",
  // Basic web fallback
  "Helvetica Neue", Arial, sans-serif,
  // Emoji fonts
  "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol" !default;
{% endhighlight %}

이 `font-family` 는 `<body>` 에 적용되고 자동으로 부트스트랩을 통해 전역으로 상속됩니다. 전역 `font-family` 을 바꾸려면, `$font-family-base` 을 업데이트 하고 부트스트랩을 다시 컴파일하세요.

## 제목과 단락

`<h1>` 과 같은 모든 제목 요소와 `<p>` 는 `margin-top` 이 제거되도록 재설정됩니다. 간편한 간격 조정을 위해 제목은 `margin-bottom: .5rem`, 단락은 `margin-bottom: 1rem` 이 추가되었습니다.

<table>
  <thead>
    <tr>
      <th>제목</th>
      <th>예제</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        {{ "`<h1></h1>`" | markdownify }}
      </td>
      <td><span class="h1">h1. 부트스트랩 제목</span></td>
    </tr>
    <tr>
      <td>
        {{ "`<h2></h2>`" | markdownify }}
      </td>
      <td><span class="h2">h2. 부트스트랩 제목</span></td>
    </tr>
    <tr>
      <td>
        {{ "`<h3></h3>`" | markdownify }}
      </td>
      <td><span class="h3">h3. 부트스트랩 제목</span></td>
    </tr>
    <tr>
      <td>
        {{ "`<h4></h4>`" | markdownify }}
      </td>
      <td><span class="h4">h4. 부트스트랩 제목</span></td>
    </tr>
    <tr>
      <td>
        {{ "`<h5></h5>`" | markdownify }}
      </td>
      <td><span class="h5">h5. 부트스트랩 제목</span></td>
    </tr>
    <tr>
      <td>
        {{ "`<h6></h6>`" | markdownify }}
      </td>
      <td><span class="h6">h6. 부트스트랩 제목</span></td>
    </tr>
  </tbody>
</table>

## 목록

`<ul>`, `<ol>`, `<dl>` 과 같은 모든 목록은 `margin-top` 이 제거되며 `margin-bottom: 1rem` 이 적용됩니다. 중첩된 목록은 `margin-bottom` 이 없습니다.

<div class="bd-example">
{% capture markdown %}
* Lorem ipsum dolor sit amet
* Consectetur adipiscing elit
* Integer molestie lorem at massa
* Facilisis in pretium nisl aliquet
* Nulla volutpat aliquam velit
  * Phasellus iaculis neque
  * Purus sodales ultricies
  * Vestibulum laoreet porttitor sem
  * Ac tristique libero volutpat at
* Faucibus porta lacus fringilla vel
* Aenean sit amet erat nunc
* Eget porttitor lorem

1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa
4. Facilisis in pretium nisl aliquet
5. Nulla volutpat aliquam velit
6. Faucibus porta lacus fringilla vel
7. Aenean sit amet erat nunc
8. Eget porttitor lorem
{% endcapture %}
{{ markdown | markdownify }}
</div>

보다 단순한 스타일, 명확한 계층구조 및 더 나은 간격조정을 위해 정의형 목록은 `margin` 이 업데이트 되었습니다. `<dd>` 는 `margin-left` 이 `0` 으로 재설정되었고 `margin-bottom: .5rem` 이 추가되었습니다. `<dt>` 는 **굵게** 표시됩니다.

<div class="bd-example">
  <dl>
    <dt>Description lists</dt>
    <dd>A description list is perfect for defining terms.</dd>
    <dt>Euismod</dt>
    <dd>Vestibulum id ligula porta felis euismod semper eget lacinia odio sem.</dd>
    <dd>Donec id elit non mi porta gravida at eget metus.</dd>
    <dt>Malesuada porta</dt>
    <dd>Etiam porta sem malesuada magna mollis euismod.</dd>
  </dl>
</div>

## 서식화된 텍스트

`<pre>` 요소는 `margin-top` 을 제거하고 `margin-bottom` 에 `rem` 단위를 사용하도록 재설정됩니다.

<div class="bd-example">
<pre>
.example-element {
  margin-bottom: 1rem;
}
</pre>
</div>

## 테이블

테이블은 `<caption>` 에 스타일을 지정하고, 테두리를 상쇄하고, 전체적으로 일관된 `text-align` 을 유지하도록 미세하게 조정되었습니다. 테두리와 패딩 등에 대한 추가적인 변경사항은 [`.table` 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/content/tables/) 와 함께 제공됩니다.  

<div class="bd-example">
  <table>
    <caption>
      This is an example table, and this is its caption to describe the contents.
    </caption>
    <thead>
      <tr>
        <th>Table heading</th>
        <th>Table heading</th>
        <th>Table heading</th>
        <th>Table heading</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Table cell</td>
        <td>Table cell</td>
        <td>Table cell</td>
        <td>Table cell</td>
      </tr>
      <tr>
        <td>Table cell</td>
        <td>Table cell</td>
        <td>Table cell</td>
        <td>Table cell</td>
      </tr>
      <tr>
        <td>Table cell</td>
        <td>Table cell</td>
        <td>Table cell</td>
        <td>Table cell</td>
      </tr>
    </tbody>
  </table>
</div>

## 폼

더 간단한 기본 스타일을 위해 다양한 폼 요소가 reboot 되었습니다. 다음은 가장 주목할만한 변경사항입니다.

- `<fieldset>` 은 테두리, 패딩, 여백을 가지지 않기 때문에 개별 입력이나 입력 그룹을 위한 wrapper 로 쉽게 사용할 수 있습니다. 
- `<legend>` 는 fieldset 과 비슷하게 제목처럼 표시되도록 스타일이 다시 지정되었습니다.
- `<label>` 은 `margin` 을 적용할 수 있도록 `display: inline-block` 이 적용 되었습니다.
- `<input>`, `<select>`, `<textarea>`, `<button>` 는 대부분 Normalize 에서 처리되지만, Reboot 가 그들의 `margin` 을 제거하고 `line-height: inherit` 를 설정합니다.
- `<textarea>` 는 가로 크기 조정이 종종 페이지 레이아웃을 "깨지게" 하기 때문에 세로로만 크기를 조정할 수 있도록 수정됬습니다.

이러한 변경사항들은 아래에서 확인할 수 있습니다.

<form class="bd-example">
  <fieldset>
    <legend>Example legend</legend>

    <p>
      <label for="input">Example input</label>
      <input type="text" id="input" placeholder="Example input">
    </p>

    <p>
      <label for="select">Example select</label>
      <select id="select">
        <option value="">Choose...</option>
        <optgroup label="Option group 1">
          <option value="">Option 1</option>
          <option value="">Option 2</option>
          <option value="">Option 3</option>
        </optgroup>
        <optgroup label="Option group 2">
          <option value="">Option 4</option>
          <option value="">Option 5</option>
          <option value="">Option 6</option>
        </optgroup>
      </select>
    </p>

    <p>
      <label>
        <input type="checkbox" value="">
        Check this checkbox
      </label>
    </p>

    <p>
      <label>
        <input type="radio" name="optionsRadios" id="optionsRadios1" value="option1" checked>
        Option one is this and that
      </label>
      <label>
        <input type="radio" name="optionsRadios" id="optionsRadios2" value="option2">
        Option two is something else that's also super long to demonstrate the wrapping of these fancy form controls.
      </label>
      <label>
        <input type="radio" name="optionsRadios" id="optionsRadios3" value="option3" disabled>
        Option three is disabled
      </label>
    </p>

    <p>
      <label for="textarea">Example textarea</label>
      <textarea id="textarea" rows="3"></textarea>
    </p>

    <p>
      <label for="date">Example date</label>
      <input type="date" id="date">
    </p>

    <p>
      <label for="time">Example time</label>
      <input type="time" id="time">
    </p>

    <p>
      <label for="output">Example output</label>
      <output name="result" id="output">100</output>
    </p>

    <p>
      <button type="submit">Button submit</button>
      <input type="submit" value="Input submit button">
      <input type="button" value="Input button">
    </p>

    <p>
      <button type="submit" disabled>Button submit</button>
      <input type="submit" value="Input submit button" disabled>
      <input type="button" value="Input button" disabled>
    </p>
  </fieldset>
</form>

## 기타 요소

### 주소

`<address>` 요소는 브라우저 `font-style` 기본값을 `italic` 에서 `normal` 로 재설정하도록 업데이트 되었습니다. `line-height` 도 또한 상속되며, `margin-bottom: 1rem` 이 추가되었습니다. `<address>` 는 상위에 인접하는 내용(혹은 전체 본문)에 대한 연락처 정보를 제공하기 위한 것입니다. `<br>` 으로 개행합니다.

<div class="bd-example">
  <address>
    <strong>Twitter, Inc.</strong><br>
    1355 Market St, Suite 900<br>
    San Francisco, CA 94103<br>
    <abbr title="Phone">P:</abbr> (123) 456-7890
  </address>

  <address>
    <strong>Full Name</strong><br>
    <a href="mailto:#">first.last@example.com</a>
  </address>
</div>

### 인용문

blockquote 의 기본 `margin` 은 `1em 40px` 이므로 다른 요소와 일관성을 위해 `0 0 1rem` 으로 재설정합니다.

<div class="bd-example">
  <blockquote class="blockquote">
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
    <footer>Someone famous in <cite title="Source Title">Source Title</cite></footer>
  </blockquote>
</div>

### 인라인 요소

`<abbr>` 요소는 단락 텍스트 사이에서 눈에 띄도록 기본 스타일을 적용합니다.

<div class="bd-example">
  Nulla <abbr title="attribute">attr</abbr> vitae elit libero, a pharetra augue.
</div>

### Summary

summary 의 `cursor` 기본값은 `text` 이므로 요소를 클릭하면 상호 작요할 수 있음을 전달하기 위해 `pointer` 로 재설정합니다.

<div class="bd-example">
  <details>
    <summary>Some details</summary>
    <p>More info about the details.</p>
  </details>

  <details open>
    <summary>Even more details</summary>
    <p>Here are even more details about the details.</p>
  </details>
</div>

## HTML5 `[hidden]` 속성

HTML5 는 기본으로 `display: none` 의 스타일이 적용된 [`[hidden]` 이라는 새로운 전역 속성](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/hidden) 을 추가합니다. [PureCSS](https://purecss.io/) 에서 아이디어를 빌리자면, `[hidden] { display: none !important; }` 을 사용하여 `display` 가 우연히 오버라이드 되는 것을 방지합니다. `[hidden]` 은 IE10 에서 지원하지 않지만, CSS 의 명시적 선언은 그 문제를 해결합니다.

{% highlight html %}
<input type="text" hidden>
{% endhighlight %}

{% capture callout %}
##### jQuery 비호환성

`[hidden]` 은 jQuery 의 `$(...).hide()` 와 `$(...).show()` 메서드와 호환되지 않습니다. 따라서, 우리는 현재 `display` 요소를 관리하는 다른 기술보다 `[hidden]` 을 특별히 지지하지 않습니다. 
{% endcapture %}
{% include callout.html content=callout type="warning" %}

`display` 가 수정되지 않고 요소가 문서의 흐름에 영향을 주면서 단순히 요소의 가시성을 전환하려면, [`.invisible` 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/visibility/) 를 대신 사용하세요.
