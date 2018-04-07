---
layout: docs
title: 브라우저와 기기
description: 부트스트랩에 의해 지원되는, 예전부터 현재까지, 브라우저와 기기들의 알려진 특이점과 버그들을 관해 알아보세요. 
group: getting-started
toc: true
---

## 지원되는 브라우저

부트스트랩은 모든 주요 브라우저와 플랫폼의 **최신, 안정 버전** 을 지원합니다. 윈도우즈에서는 **인터넷 익스플로러 10-11 / 마이크로소프트 엣지를 지원합니다**.

직접 혹은 플랫폼의 웹뷰 API 를 통한, WebKit, Blink, Gecko 의 최신 버전을 사용하는 대안 브라우저는 명시적으로 지원되지는 않습니다. 하지만, 부트스트랩은 이런 브라우저에서도 물론 정확하게 표시되고 동작합니다. 더 명확한 지원 정보는 아래에 제공됩니다.   

### 모바일 기기

일반적으로 말하자면, 부트스트랩은 각각의 주요 플랫폼의 기본 브라우저 최신 버전을 지원합니다. 프록시 브라우저 (오페라 미니, 오페라 모바일의 터보 모드, UC 브라우저 미니, 아마존 실크) 는 지원되지 않습니다.  

<table class="table table-bordered table-striped">
  <thead>
    <tr>
      <td></td>
      <th>크롬</th>
      <th>파이어폭스</th>
      <th>사파리</th>
      <th>안드로이드 브라우저 &amp; 웹뷰</th>
      <th>마이크로소프트 엣지</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">안드로이드</th>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-success">안드로이드 v5.0+ 지원됨</td>
      <td class="text-success">지원됨</td>
    </tr>
    <tr>
      <th scope="row">iOS</th>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-success">지원됨</td>
    </tr>
    <tr>
      <th scope="row">윈도우즈 10 모바일</th>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-success">지원됨</td>
    </tr>
  </tbody>
</table>

### 데스크탑 브라우저

마찬가지로, 대부분의 데스크탑 브라우저의 최신 버전은 지원됩니다.

<table class="table table-bordered table-striped">
  <thead>
    <tr>
      <td></td>
      <th>크롬</th>
      <th>파이어폭스</th>
      <th>인터넷 익스플로러</th>
      <th>마이크로소프트 엣지</th>
      <th>오페라</th>
      <th>사파리</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">맥</th>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-muted">해당하지 않음</td>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
    </tr>
    <tr>
      <th scope="row">윈도우즈</th>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-success">IE10+ 지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-success">지원됨</td>
      <td class="text-danger">미지원</td>
    </tr>
  </tbody>
</table>

파이어폭스의 경우, 보통의 최신 안정 버전에 덧붙여, 최신 [Extended Support Release (ESR)](https://www.mozilla.org/en-US/firefox/organizations/faq/) 도 지원합니다.

비공식적으로, 부트스트랩은 리눅스를 위한 크로미엄과 크롬, 리눅스를 위한 파이어폭스, 인터넷 익스플로러 9 에서 잘 보여지고 동작해야하지만, 공식적으로 지원되는 것은 아닙니다.

부트스트랩이 해결해야하는 브라우저 버그의 목록은 [브라우저 버그 담벼락]({{ site.baseurl }}/docs/{{ site.docs_version }}/browser-bugs/) 을 보세요.

## 인터넷 익스플로러

인터넷 익스플로러 10+ 는 지원됩니다. IE9 이하는 지원되지 않습니다. 일부 CSS3 속성과 HTML 요소들은 IE10 에서 완전하게 지원되지 않으며, 완전한 동작을 위해 접두사가 붙은 속성을 필요로 하는 것을 유념해주세요. CSS3 와 HTML 기능의 브라우저 지원에 대한 자세한 사항은 [Can I use...](https://caniuse.com/) 를 방문해주세요. 

**만약 IE8-9 지원이 필요하다면, 부트스트랩 3 를 사용하세요.** 그것은 가장 안정적인 버전이고 치명적인 버그 수정 및 설명서 변경들은 우리팀에 의해 여전히 지원됩니다. 하지만 새로운 기능은 추가되지 않습니다.

## 모바일에서 모달과 드롭다운

### Overflow 와 스크롤하기

iOS 와 안드로이드에서 `<body>` 요소의 `overflow: hidden;` 에 대한 지원은 상당히 제한적입니다. 
그 결과, 그 기기들의 브라우저에서 상단이나 하단을 지나 스크롤 되면, `<body>` 가 스크롤 되기 시작할 것입니다.
 
[크롬 버그 #175502](https://bugs.chromium.org/p/chromium/issues/detail?id=175502) (크롬 v40 에서 수정됨) 와 [웹킷 버그 #153852](https://bugs.webkit.org/show_bug.cgi?id=153852) 를 참조하세요.

### iOS 텍스트 필드와 스크롤하기

iOS 9.2 이래로, 모달이 열려있는 동안, 스크롤 제스처의 첫 터치가 `<input>` 나 `<textarea>` 에 경계 내에 있다면, 모달 아래의 `<body>` 내용이 모달 대신 스크롤 될 것입니다. [웹킷 버그 #153856](https://bugs.webkit.org/show_bug.cgi?id=153856) 를 참조하세요.

### Navbar 드롭다운

nav 의 `.dropdown-backdrop` 요소는 z-indexing 복잡성으로 인해 iOS 에서 사용되지 않습니다. 따라서 navbars 에서 드롭다운을 닫으려면, 드롭다운 요소 (혹은 [iOS 에서 클릭 이벤트를 발생하는 어느 다른 요소](https://developer.mozilla.org/en-US/docs/Web/Events/click#Safari_Mobile)) 를 직접 클릭해야 합니다.

## 브라우저 확대/축소

부트스트랩이나 다른 웹사이트 모두, 페이지 확대/축소는 필연적으로 일부 컴포넌트에서 렌더링 부산물을 보여줍니다. 어떤 이슈냐에 따라, 그것을 고칠 수도 있습니다. (우선 검색해보고 필요하다면 이슈를 열어서). 하지만, 우리는 다른 마땅한 해결책이 없는 만큼 이것들을 무시하는 경향이 있습니다

## iOS 에서의 끈적한 `:hover`/`:focus`

대부분의 터치 기기에서 `:hover` 는 가능하지 않는 반면, iOS 는 이 동작을 한 요소를 탭한 후에 hover 스타일이 지속되도록 "끈적하게" 에뮬레이트합니다. 이 hover 스타일은 오직 사용자가 다른 요소를 탭했을 때 제거됩니다. 이 동작은 크게 바람직하지 않은 것으로 간주되며 안드로이드나 윈도우즈 기기에서는 문제가 발생하지 않는 것으로 보입니다. 

v4 알파와 베타 버전동안, 우리는 미완성을 포함하고, hovering 을 에뮬레이트하는 터치 기기 브라우저에서 hover 스타일을 비활성화 하는 미디어 쿼리 shim 을 적용하는 코드를 주석처리하였습니다. 이 작업은 결코 완전히 완성되거나 활성화된 것은 아니지만, 완전히 망가지는 것을 피합니다. 우리는 [이 shim](https://github.com/twbs/mq4-hover-shim) 을 사용하지 않는 것을 선택하고 가상클래스를 위한 믹스인을 가지도록 하였습니다.

## 인쇄

일부 현대 브라우저에서조차, 인쇄는 이상해질 수 있습니다.

사파리 v8.0 이래로, 고정폭 `.container` 의 사용은 인쇄시 사파리가 몹시 작은 폰트 사이즈를 사용하게 유발합니다. 자세한 것은 [이슈 #14868]({{ site.repo }}/issues/14868) 와 [웹킷 버그 #138192](https://bugs.webkit.org/show_bug.cgi?id=138192) 를 참조하세요. 가능성이 있는 차선책은 다음과 같습니다.

{% highlight css %}
@media print {
  .container {
    width: auto;
  }
}
{% endhighlight %}

## 안드로이드 스톡 브라우저

특별히, 안드로이드 4.1 (및 일부 최신 버전에서도) 은 스톡 브라우저 앱을 기본 웹브라우저로 제공합니다. 불행하게도, 스톡 브라우저 앱은 전반적으로 CSS 관련하여 많은 버그와 비일관성을 가지고 있습니다.

#### 셀렉트 메뉴

`<select>` 요소에서, 안드로이드 스톡 브라우저는 `border-radius` 나 `border` 가 적용되었다면 사이드 콘트롤을 표시하지 않습니다. (자세한 것은 [이 스택오버플로어 질문](https://stackoverflow.com/questions/14744437/html-select-box-not-showing-drop-down-arrow-on-android-version-4-0-when-set-with) 을 참조하세요.) 문제가 되는 CSS 를 제거하고 `<select>` 를 안드로이드 스톡 브라우저에서 스타일 없는 요소로 보여지게 하려면 아래의 코드 조각을 사용하세요. 사용자 에이전트 스니핑은 크롬, 사파리, 모질라 브라우저들은 제외합니다.

{% highlight html %}
<script>
$(function () {
  var nua = navigator.userAgent
  var isAndroid = (nua.indexOf('Mozilla/5.0') > -1 && nua.indexOf('Android ') > -1 && nua.indexOf('AppleWebKit') > -1 && nua.indexOf('Chrome') === -1)
  if (isAndroid) {
    $('select.form-control').removeClass('form-control').css('width', '100%')
  }
})
</script>
{% endhighlight %}

예제를 보고 싶으신가요? [이 데모를 확인해보세요.](http://jsbin.com/OyaqoDO/2)

## 유효성 검사기

오래되고 버그 많은 브라우저들에게 최대한 긍정적인 경험을 제공하기 위해, 부트스트랩은 브라우저들의 버그를 우회하기 위해서 몇군데에 특정 브라우저 버전에 특별한 CSS 를 지정하고자 하는 [CSS 브라우저 핵](http://browserhacks.com/) 을 사용합니다. 이 핵들은 당연하게도 CSS 검사기가 그들은 유효하지 않다고 제기하도록 합니다. 두군데에서, 우리는 또한 아직 표준화되지 않은 최신의 CSS 기능을 사용합니다. 그러나 그들은 전적으로 점진적인 향상을 위해 사용되어집니다.

이 검사기 경고들은 핵을 쓰지 않은 우리의 CSS 부분이 전부 검사되고 핵을 쓴 부분은 제대로 된 기능에 간섭하지 않으므로, 실제로는 문제가 되지 않습니다. 이런 이유로 우리는 그 특정한 경고들을 의도적으로 무시합니다.

우리의 HTML 문서들도 [특정 파이어폭스 버그](https://bugzilla.mozilla.org/show_bug.cgi?id=654072) 를 해결하기 위한 코드로 인하여 몇개의 사소하고 중요하지 않은 HTML 검사기 경고들을 가지고 있습니다.
