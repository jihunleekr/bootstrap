---
layout: docs
title: 타이포그래피
description: 전역 설정, 제목, 본문, 목록 등을 포함한 부트스트랩 타이포그래피에 대한 설명서와 예제.
group: content
toc: true
---

## 전역 설정

부트스트랩은 전역 디스플레이, 타이포그래피, 링크 스타일을 설정합니다. 더 많은 제어가 필요하면, [텍스트 유틸리티 클래스]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/text/) 을 확인하세요.

- 각 OS 와 장치에 가장 적합한 `font-family` 를 선택하는 [기본 글꼴 스택]({{ site.baseurl }}/docs/{{ site.docs_version }}/content/reboot/#기본-글꼴-스택) 을 사용하세요.
- 더 포괄적이고 이해하기 쉬운 글꼴 크기 조정을 위해, 우리는 방문자가 필요에 따라 브라우저 기본값을 맞춤화할 수 있도록 브라우저 최상위 `font-size` 기본값 (일반적으로 16px) 을 사용합니다.
- `<body>` 에 적용될 타이포그래피 기본값을 설정하기 위해 `$font-family-base`, `$font-size-base`, `$line-height-base` 를 사용하세요.
- `$link-color` 로 전역 링크색을 설정하고 `:hover` 에만 링크 밑줄을 적용하세요.
- `$body-bg` 를 사용하여 `<body>` 의 `background-color` 를 설정하세요 (기본적으로 `#fff`).

이 스타일들은 `_reboot.scss` 내에서 찾을 수 있고, 전역 변수들은 `_variables.scss` 에 정의되어 있습니다. `$font-size-base` 는 `rem` 으로 설정해야 하는 것을 명심하세요.

## 제목

모든 HTML 제목, `<h1>` 부터 `<h6>` 까지 사용할 수 있습니다.

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

{% highlight html %}
<h1>h1. 부트스트랩 제목</h1>
<h2>h2. 부트스트랩 제목</h2>
<h3>h3. 부트스트랩 제목</h3>
<h4>h4. 부트스트랩 제목</h4>
<h5>h5. 부트스트랩 제목</h5>
<h6>h6. 부트스트랩 제목</h6>
{% endhighlight %}

또한 제목 글꼴 스타일을 원하지만 연관된 HTML 요소를 사용할 수 없을 때를 위해 `.h1` 부터 `.h6` 클래스를 사용할 수 있습니다.

{% capture example %}
<p class="h1">h1. 부트스트랩 제목</p>
<p class="h2">h2. 부트스트랩 제목</p>
<p class="h3">h3. 부트스트랩 제목</p>
<p class="h4">h4. 부트스트랩 제목</p>
<p class="h5">h5. 부트스트랩 제목</p>
<p class="h6">h6. 부트스트랩 제목</p>
{% endcapture %}
{% include example.html content=example %}

### 제목 맞춤화

포함된 유틸리티 클래스를 사용하여 부트스트랩 3 의 작은 보조 제목을 재현해보세요.

<div class="bd-example">
  <span class="h3">
    멋진 제목
    <small class="text-muted">희미한 부제목 텍스트</small>
  </span>
</div>

{% highlight html %}
<h3>
  멋진 제목
  <small class="text-muted">희미한 부제목 텍스트</small>
</h3>
{% endhighlight %}

## 디스플레이 제목

기존 제목 요소는 페이지 콘텐츠에서 가장 잘 작동하도록 설계되었습니다.
눈에 띄는 제목이 필요할 때, 좀 더 독창적인 제목 스타일인 **display heading** 을 사용하는 것을 고려해보세요.

<div class="bd-example bd-example-type">
  <table class="table">
    <tbody>
      <tr>
        <td><span class="display-1">Display 1</span></td>
      </tr>
      <tr>
      <td><span class="display-2">Display 2</span></td>
      </tr>
      <tr>
      <td><span class="display-3">Display 3</span></td>
      </tr>
      <tr>
      <td><span class="display-4">Display 4</span></td>
      </tr>
    </tbody>
  </table>
</div>

{% highlight html %}
<h1 class="display-1">Display 1</h1>
<h1 class="display-2">Display 2</h1>
<h1 class="display-3">Display 3</h1>
<h1 class="display-4">Display 4</h1>
{% endhighlight %}

## 리드 단락

단락에 `.lead` 를 추가하여 눈에 띄게 만드세요.

{% capture example %}
<p class="lead">
  Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus.
</p>
{% endcapture %}
{% include example.html content=example %}

## 인라인 텍스트 요소

일반적인 인라인 HTML 요소들을 위한 스타일링.

{% capture example %}
<p>mark 태그를 사용하여 텍스트를 <mark>강조</mark> 할 수 있습니다.</p>
<p><del>이 텍스트 줄은 삭제된 텍스트로 간주됩니다.</del></p>
<p><s>이 텍스트 줄은 더 이상 정확하지 않은 것으로 간주됩니다.</s></p>
<p><ins>이 텍스트 줄은 문서에 추가분으로 간주됩니다.</ins></p>
<p><u>이 텍스트 줄은 밑줄이 그어질 것입니다.</u></p>
<p><small>이 텍스트 줄은 작게 출력되는 것을 의미합니다.</small></p>
<p><strong>이 줄은 굵은 텍스트로 표시됩니다.</strong></p>
<p><em>이 줄은 기울임 텍스트로 표시됩니다.</em></p>
{% endcapture %}
{% include example.html content=example %}

`.mark` 와 `.small` 클래스도 사용가능하며 `<mark>` 와 `<small>` 와 같은 스타일을 적용하면서 태그가 가져다주는 원치 않는 시맨틱한 영향을 피합니다.

위에 제시되지는 않았지만, HTML5 에서 `<b>` 와 `<i>` 를 마음놓고 사용하셔도 됩니다.
`<b>` 는 단어나 문구를 강조하는 것을 의미하고 `<i>` 는 거의 음성, 기술 용어 등을 위한 것입니다.

## 텍스트 유틸리티

[텍스트 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/text/) 와 [색 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/colors/) 로 텍스트 정렬, 변형, 스타일, 두께, 색상을 변경하세요.

## 약어

약어나 두문자어에 커서를 올렸을 때 확장된 버전을 보여주기 위해 `<abbr>` 요소의 스타일이 적용된 구현. 약어는 기본적으로 밑줄이 있으며 커서를 올렸을 때와 보조 기술 사용자들에게 추가적인 컨텍스트를 제공하기 위해 도움말 커서를 가집니다. 

좀 더 작은 글꼴 크기를 위해 약어에 `.initialism` 를 추가하세요.

{% capture example %}
<p><abbr title="attribute">attr</abbr></p>
<p><abbr title="HyperText Markup Language" class="initialism">HTML</abbr></p>
{% endcapture %}
{% include example.html content=example %}

## 인용구

당신의 문서 내에서 다른 자료에서 가져온 내용을 인용하기 위함.
인용할 <abbr title="HyperText Markup Language">HTML</abbr> 주위에 `<blockquote class="blockquote">` 을 둘러쌉니다.

{% capture example %}
<blockquote class="blockquote">
  <p class="mb-0">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
</blockquote>
{% endcapture %}
{% include example.html content=example %}

### 출처 표기

출처를 식별하기 위해 `<footer class="blockquote-footer">` 를 추가하세요. `<cite>` 에 출처를 입력하세요.

{% capture example %}
<blockquote class="blockquote">
  <p class="mb-0">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
  <footer class="blockquote-footer">Someone famous in <cite title="Source Title">Source Title</cite></footer>
</blockquote>
{% endcapture %}
{% include example.html content=example %}

### 정렬

인용구 정렬을 위해 텍스트 유틸리티를 사용하세요.

{% capture example %}
<blockquote class="blockquote text-center">
  <p class="mb-0">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
  <footer class="blockquote-footer">Someone famous in <cite title="Source Title">Source Title</cite></footer>
</blockquote>
{% endcapture %}
{% include example.html content=example %}

{% capture example %}
<blockquote class="blockquote text-right">
  <p class="mb-0">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
  <footer class="blockquote-footer">Someone famous in <cite title="Source Title">Source Title</cite></footer>
</blockquote>
{% endcapture %}
{% include example.html content=example %}

## 목록

### 스타일 없음

기본 `list-style` 과 목록 항목 (가장 가까운 하위 항목들만) 의 왼쪽 여백을 제거하세요. **가장 가까운 하위 목록 항목들에만 적용되기 때문에**, 중첩된 목록에도 클래스를 추가하는 것이 필요할 것입니다. 

{% capture example %}
<ul class="list-unstyled">
  <li>Lorem ipsum dolor sit amet</li>
  <li>Consectetur adipiscing elit</li>
  <li>Integer molestie lorem at massa</li>
  <li>Facilisis in pretium nisl aliquet</li>
  <li>Nulla volutpat aliquam velit
    <ul>
      <li>Phasellus iaculis neque</li>
      <li>Purus sodales ultricies</li>
      <li>Vestibulum laoreet porttitor sem</li>
      <li>Ac tristique libero volutpat at</li>
    </ul>
  </li>
  <li>Faucibus porta lacus fringilla vel</li>
  <li>Aenean sit amet erat nunc</li>
  <li>Eget porttitor lorem</li>
</ul>
{% endcapture %}
{% include example.html content=example %}

### 인라인

`.list-inline` 과 `.list-inline-item` 의 조합으로 목록의 기호를 제거하고 약간의 `margin` 을 적용합니다.

{% capture example %}
<ul class="list-inline">
  <li class="list-inline-item">Lorem ipsum</li>
  <li class="list-inline-item">Phasellus iaculis</li>
  <li class="list-inline-item">Nulla volutpat</li>
</ul>
{% endcapture %}
{% include example.html content=example %}

### 정의형 목록 정렬

그리드 시스템의 미리 정의된 클래스 (혹은 시맨틱 믹스인) 를 이용하여 용어와 설명을 수평적으로 정렬하세요. 긴 용어의 경우, `.text-truncate` 를 추가하여 말줄임표와 함께 텍스트를 짧게할 수 있습니다.

{% capture example %}
<dl class="row">
  <dt class="col-sm-3">Description lists</dt>
  <dd class="col-sm-9">A description list is perfect for defining terms.</dd>

  <dt class="col-sm-3">Euismod</dt>
  <dd class="col-sm-9">
    <p>Vestibulum id ligula porta felis euismod semper eget lacinia odio sem nec elit.</p>
    <p>Donec id elit non mi porta gravida at eget metus.</p>
  </dd>

  <dt class="col-sm-3">Malesuada porta</dt>
  <dd class="col-sm-9">Etiam porta sem malesuada magna mollis euismod.</dd>

  <dt class="col-sm-3 text-truncate">Truncated term is truncated</dt>
  <dd class="col-sm-9">Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</dd>

  <dt class="col-sm-3">Nesting</dt>
  <dd class="col-sm-9">
    <dl class="row">
      <dt class="col-sm-4">Nested definition list</dt>
      <dd class="col-sm-8">Aenean posuere, tortor sed cursus feugiat, nunc augue blandit nunc.</dd>
    </dl>
  </dd>
</dl>
{% endcapture %}
{% include example.html content=example %}

## 반응형 타이포그래피

*반응형 타이포그래피* 는 일련의 미디어 쿼리 내에서 최상위 요소의 `font-size` 를 간단하게 조정하여 텍스트와 컴포넌트의 크기를 조정하는 것을 의미합니다. 부트스트랩은 이 작업을 수행하지 않지만 필요한 경우 쉽게 추가할 수 있습니다.

다음은 실제 예시입니다. 원하는 `font-size` 와 미디어 쿼리를 선택하세요.

{% highlight scss %}
html {
  font-size: 1rem;
}

@include media-breakpoint-up(sm) {
  html {
    font-size: 1.2rem;
  }
}

@include media-breakpoint-up(md) {
  html {
    font-size: 1.4rem;
  }
}

@include media-breakpoint-up(lg) {
  html {
    font-size: 1.6rem;
  }
}
{% endhighlight %}
