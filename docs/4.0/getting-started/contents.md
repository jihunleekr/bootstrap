---
layout: docs
title: 내용
description: 미리 컴파일된 소스코드 등 부트스트랩에 무엇이 있는지 찾아보세요. 기억하세요, 부트스트랩의 자바스크립트 플러그인은 jQuery 가 필요합니다.
group: getting-started
toc: true
---

## 미리 컴파일된 부트스트랩

다운로드한 다음, 압축된 폴더를 풀면 다음과 같은 것들을 볼 수 있습니다.

<!-- NOTE: This info is intentionally duplicated in the README. Copy any changes made here over to the README too. -->

{% highlight plaintext %}
bootstrap/
├── css/
│   ├── bootstrap.css
│   ├── bootstrap.css.map
│   ├── bootstrap.min.css
│   ├── bootstrap.min.css.map
│   ├── bootstrap-grid.css
│   ├── bootstrap-grid.css.map
│   ├── bootstrap-grid.min.css
│   ├── bootstrap-grid.min.css.map
│   ├── bootstrap-reboot.css
│   ├── bootstrap-reboot.css.map
│   ├── bootstrap-reboot.min.css
│   └── bootstrap-reboot.min.css.map
└── js/
    ├── bootstrap.bundle.js
    ├── bootstrap.bundle.min.js
    ├── bootstrap.js
    └── bootstrap.min.js
{% endhighlight %}

이것은 대부분의 웹프로젝트에서 빠른 사용을 위해 미리 컴파일된 파일들인 부트스트랩의 기본 모습입니다. 우리는 컴파일되고 압축된 CSS 와 JS (`bootstrap.min.*`) 뿐만 아니라, 컴파일만 된 CSS 와 JS (`bootstrap.*`) 도 제공합니다. CSS [소스맵](https://developers.google.com/web/tools/chrome-devtools/javascript/source-maps) (`bootstrap.*.map`) 은 특정 브라우저의 개발도구와 함께 사용이 가능합니다. 묶음된 JS 파일들은 (`bootstrap.bundle.js` 와 압축된 `bootstrap.bundle.min.js`) [Popper](https://popper.js.org/) 를 포함하지만, [jQuery](https://jquery.com/) 를 포함하지 않습니다.

## CSS 파일

부트스트랩은 컴파일된 CSS 의 일부 혹은 전부를 포함할 것인지에 대해 약간의 선택사항을 제공합니다.

<table class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">CSS 파일</th>
      <th scope="col">레이아웃</th>
      <th scope="col">내용</th>
      <th scope="col">콤포넌트</th>
      <th scope="col">유틸리티</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">
        <div><code class="font-weight-normal text-nowrap">bootstrap.css</code></div>
        <div><code class="font-weight-normal text-nowrap">bootstrap.min.css</code></div>
      </th>
      <td class="text-success">포함</td>
      <td class="text-success">포함</td>
      <td class="text-success">포함</td>
      <td class="text-success">포함</td>
    </tr>
    <tr>
      <th scope="row">
        <div><code class="font-weight-normal text-nowrap">bootstrap-grid.css</code></div>
        <div><code class="font-weight-normal text-nowrap">bootstrap-grid.min.css</code></div>
      </th>
      <td><a class="text-warning" href="{{ site.baseurl }}/docs/{{ site.docs_version }}/layout/grid/">그리드 시스템만</a></td>
      <td class="bg-light text-muted">미포함</td>
      <td class="bg-light text-muted">미포함</td>
      <td><a class="text-warning" href="{{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/flex/">flex 유틸리티만</a></td>
    </tr>
    <tr>
      <th scope="row">
        <div><code class="font-weight-normal text-nowrap">bootstrap-reboot.css</code></div>
        <div><code class="font-weight-normal text-nowrap">bootstrap-reboot.min.css</code></div>
      </th>
      <td class="bg-light text-muted">미포함</td>
      <td><a class="text-warning" href="{{ site.baseurl }}/docs/{{ site.docs_version }}/content/reboot/">Reboot 만</a></td>
      <td class="bg-light text-muted">미포함</td>
      <td class="bg-light text-muted">미포함</td>
    </tr>
  </tbody>
</table>

## JS 파일

유사하게, 우리는 컴파일된 자바스크립트도 일부 혹은 전체를 포함하는 것에 대해 선택사항을 가집니다.

<table class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">JS 파일</th>
      <th scope="col">Popper</th>
      <th scope="col">jQuery</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">
        <div><code class="font-weight-normal text-nowrap">bootstrap.bundle.js</code></div>
        <div><code class="font-weight-normal text-nowrap">bootstrap.bundle.min.js</code></div>
      </th>
      <td class="text-success">포함</td>
      <td class="bg-light text-muted">미포함</td>
    </tr>
    <tr>
      <th scope="row">
        <div><code class="font-weight-normal text-nowrap">bootstrap.js</code></div>
        <div><code class="font-weight-normal text-nowrap">bootstrap.min.js</code></div>
      </th>
      <td class="bg-light text-muted">미포함</td>
      <td class="bg-light text-muted">미포함</td>
    </tr>
  </tbody>
</table>

## 부트스트랩 소스 코드

부트스트랩 소스 코드 다운로드는 Sass, 자바스크립트, 설명서 소스와 함께 미리 컴파일된 CSS 와 자바스크립트 자산을 포함합니다. 더 구체적으로, 다음과 같습니다.

{% highlight plaintext %}
bootstrap/
├── dist/
│   ├── css/
│   └── js/
├── docs/
│   └── examples/
├── js/
└── scss/
{% endhighlight %}

`scss/` 와 `js/` 는 우리의 CSS 와 자바스크립트 소스 코드 입니다. `dist/` 폴더는 위 미리 컴파일된 다운로드 섹션의 모든 목록을 포함합니다. `docs/` 폴더는 설명서 소스 코드를, `examples/` 는 부트스트랩 예제를 포함합니다. 그밖에, 포함된 다른 파일들은 패키지, 라이센스 정보, 개발 등을 제공합니다.
