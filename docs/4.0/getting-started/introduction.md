---
layout: docs
title: 소개
description: 부트스트랩 CDN 과 초심자 템플릿으로 부트스트랩으로 시작해보세요. 부트스트랩은 반응형, 모바일 우선 사이트를 위한 세계에서 가장 인기있는 프레임워크입니다.
group: getting-started
redirect_from:
  - /docs/
  - /docs/4.0/
  - /docs/4.0/getting-started/
  - /docs/getting-started/
toc: true
---

## 빠른 시작

프로젝트에 부트스트랩을 간단하게 추가하는 방법을 찾고 계세요? MaxCDN 에서 무료로 제공하는 부트스트랩 CDN 을 사용해보세요. 패키지 관리자를 사용하거나 소스 파일을 다운로드 해야하나요?  [다운로드 페이지로 이동.]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/download/)

### CSS

우리 CSS 를 불러오기 위해 `<head>` 내에 다른 스타일시트들 보다 위에 `<link>` 코드를 복사하여 붙여넣으세요.

{% highlight html %}
<link rel="stylesheet" href="{{ site.cdn.css }}" integrity="{{ site.cdn.css_hash }}" crossorigin="anonymous">
{% endhighlight %}

### JS

우리의 대다수의 컴포넌트들이 작동하려면 자바스크립트 사용이 필요합니다. 구체적으로, [jQuery](https://jquery.com), [Popper.js](https://popper.js.org/), 자바스크립트 플러그인이 필요합니다. 그것들을 활성화하기위해 페이지 하단 부근 `</body>` 태그 직전에 다음의 `<script>` 들을 넣으세요. jQuery 는 먼저 와야하며, 다음은 Popper.js, 그리고 자바스크립트 플러그인 순서입니다.

우리는 [jQuery's slim build](https://blog.jquery.com/2016/06/09/jquery-3-0-final-released/) 를 사용합니다만, 풀버전도 지원합니다.

{% highlight html %}
<script src="{{ site.cdn.jquery }}" integrity="{{ site.cdn.jquery_hash }}" crossorigin="anonymous"></script>
<script src="{{ site.cdn.popper }}" integrity="{{ site.cdn.popper_hash }}" crossorigin="anonymous"></script>
<script src="{{ site.cdn.js }}" integrity="{{ site.cdn.js_hash }}" crossorigin="anonymous"></script>
{% endhighlight %}

jQuery, 우리의 JS, Popper.js 를 명시적으로 필요로 하는 컴포넌트들이 궁금하신가요? 아래의 컴포넌트 보기 링크를 클릭하세요. 만약 일반적인 페이지 구조에 대해 완전히 이해하지 못한다면, 예제 페이지 템플릿을 계속 읽어보세요.

<details>
<summary class="text-primary mb-3">자바스크립트가 필요한 컴포넌트</summary>
{% capture markdown %}
- 알림: 닫기
- 버튼: 상태 토글과 체크박스/라디오 작동 
- 캐러셀: 모든 슬라이드 동작, 조작, 지시자
- 접기: 내용의 가시성을 토글
- 드롭다운: 표시와 위치지정 ([Popper.js](https://popper.js.org/) 도 필요함)
- 모달: 표시, 위치지정, 스크롤 동작
- 네비게이션바: 반응형 동작을 실현하기 위한 접기 플러그인을 확장
- 툴팁과 팝오버: 표시와 위치지정 ([Popper.js](https://popper.js.org/) 도 필요함)
- 스크롤감시: 스크롤 동작과 네비게이션 업데이트
{% endcapture %}
{{ markdown | markdownify }}
</details>

## 초심자 템플릿

페이지를 최신 디자인과 개발 표준으로 설정하세요. 그것은 적절한 반응형 동작을 위해 HTML5 doctype 을 사용하고 viewport 메타 태그를 포함하는 것을 의미합니다. 정리하면 페이지는 아래와 같아야 합니다.

{% highlight html %}
<!doctype html>
<html lang="en">
  <head>
    <!-- 메타 태그 필요 -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- 부트스트랩 CSS -->
    <link rel="stylesheet" href="{{ site.cdn.css }}" integrity="{{ site.cdn.css_hash }}" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- 추가적인 자바스크립트 -->
    <!-- jQuery 먼저, 다음 Popper.js, 그리고 Bootstrap JS -->
    <script src="{{ site.cdn.jquery }}" integrity="{{ site.cdn.jquery_hash }}" crossorigin="anonymous"></script>
    <script src="{{ site.cdn.popper }}" integrity="{{ site.cdn.popper_hash }}" crossorigin="anonymous"></script>
    <script src="{{ site.cdn.js }}" integrity="{{ site.cdn.js_hash }}" crossorigin="anonymous"></script>
  </body>
</html>
{% endhighlight %}

이것이 전체 페이지 요구사항의 필요한 전부입니다. 사이트의 콘텐츠와 컴포넌트를 배치하는 것을 시작하려면 [레이아웃 설명서]({{ site.baseurl }}/docs/{{ site.docs_version }}/layout/overview/) 나 [공식 예제]({{ site.baseurl }}/docs/{{ site.docs_version }}/examples/) 를 방문하세요.

## 주요한 전역 설정

부트스트랩은 사용할 때 주의가 요구되는 약간의 주요한 전역 스타일과 설정을 사용합니다. 이것들은 오직 크로스 브라우저 스타일의 정규화에 적합하도록 맞춰져있습니다. 살펴봅시다.

### HTML5 doctype

부트스트랩은 HTML5 doctype 의 사용이 필요합니다. 그것이 없으면, 불완전한 스타일링을 보게 될 것입니다만, 그것을 포함하는 것은 어떤 단점도 없습니다.

{% highlight html %}
<!doctype html>
<html lang="en">
  ...
</html>
{% endhighlight %}

### 반응형 메타태그

부트스트랩은 모바일 기기에 코드를 최적화 하고 나서 CSS 미디어 쿼리를 이용하여 필요한 만큼 컴포넌트를 확장하는 *모바일 우선* 으로 개발되어 졌습니다. 모든 기기를 위해 적절한 렌더링과 터치 줌을 보장하려면, `<head>` 에 **반응형 viewport 메타태그를 추가하세요** 

{% highlight html %}
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
{% endhighlight %}

[초심자 템플릿](#초심자-템플릿) 에서 이것이 작동하는 예제를 볼 수 있습니다.

### Box-sizing

CSS 에서 보다 간단한 크기조절을 위해, 우리는 전역 `box-sizing` 값을 `content-box` 에서 `border-box` 로 변경합니다. 이것은 `padding` 이 요소의 최종 계산된 너비에 영향을 미치지 않게 합니다. 그러나 그것은 구글맵과 구글 맞춤 검색 엔진과 같은 서드 파티 소프트웨어에서 문제를 일으킬 수 있습니다.

이런 드문 경우에는 오버라이드가 필요합니다. 다음과 같이 사용하시면 됩니다.

{% highlight css %}
.selector-for-some-widget {
  box-sizing: content-box;
}
{% endhighlight %}

위 코드조각으로, 중첩된 요소—`::before` 과 `::after` 를 통해 생성된 콘텐츠도 포함—는 `.selector-for-some-widget` 을 위해 명시된 `box-sizing` 을 상속합니다.

[CSS Tricks 의 박스 모델과 크기 조절](https://css-tricks.com/box-sizing/) 에 대하여 더 알아보세요.

### Reboot

향상된 크로스 브라우저 렌더링을 위해, 우리는 브라우저와 기기간 보통의 HTML 요소들에 좀 더 독창적인 리셋을 제공하는 대신 일관성이 없음을 고치기 위해 [Reboot]({{ site.baseurl }}/docs/{{ site.docs_version }}/content/reboot/) 를 사용합니다.

## 커뮤니티

부트스트랩 개발에 대한 최신 소식을 얻고 다음의 유용한 리소스를 통해 커뮤니티와 연락하세요.

- [트위터에서 @getbootstrap](https://twitter.com/getbootstrap) 를 팔로우합니다.
- [공식 부트스트랩 블로그]({{ site.blog }}) 를 읽고 구독합니다.
- [공식 슬랙방]({{ site.slack }}) 에 가입합니다.
- `irc.freenode.net` 서버의 `##bootstrap` 채널에서 부트스트랩을 사용하는 사람들과 대화를 나누세요.
- 구현 도움은 스택 오버플로우에서 찾을 수 있습니다. ([`bootstrap-4`](https://stackoverflow.com/questions/tagged/bootstrap-4) 태그)
- 개발자는 부트스트랩의 기능을 변경하거나 추가한 패키지를 [npm](https://www.npmjs.com/browse/keyword/bootstrap) 또는 비슷한 배포 메커니즘을 통해 배포할 때 최대한 발견될 수 있도록 `bootstrap` 키워드를 사용해야합니다. 

또한 최근 잡담과 놀라운 뮤직 비디오를 위해 [트위터에서 @getbootstrap](https://twitter.com/getbootstrap) 를 팔로우 해도 됩니다.
