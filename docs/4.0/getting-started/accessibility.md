---
layout: docs
title: 접근성
description: 부트스트랩의 기능과 접근 가능한 콘텐츠를 작성하는데 있어 제한 사항의 간략한 개요.
group: getting-started
toc: true
---

부트스트랩은 이미 만들어진 스타일, 레이아웃 도구, 대화형 컴포넌트 등의 프레임워크를 쉽게 사용할 수 있도록 제공합니다. 이는 개발자들에게 시각적으로 매력적이고 기능이 풍부하며 즉시 접근할 수 있는 웹사이트와 응용 프로그램을 만들 수 있도록 합니다. 

## 개요 및 제한사항

부트스트랩으로 만들어진 모든 프로젝트의 전반적인 접근성은 작성자의 마크업과 추가 스타일 및 스크립트에 크게 좌우됩니다. 하지만 이들이 올바르게 구현된다면, [<abbr title="웹 콘텐츠 접근성 지침">WCAG</abbr> 2.0](https://www.w3.org/TR/WCAG20/) (A/AA/AAA), [Section 508](https://www.section508.gov/) 및 비슷한 접근성 표준과 요구사항을 완벽하게 준수하는 부트스트랩 웹사이트 및 응용프로그램을 만드는 것도 가능합니다. 

### 구조적 마크업

부트스트랩의 스타일과 레이아웃은 다양한 마크업 구조에 적용될 수 있습니다. 이 설명서는 개발자에게 잠재적인 접근성 문제를 해결할 수 있는 방법을 포함하여 부트스트랩 자체의 사용법을 보여주고 적절한 시멘틱 마크업을 설명하는 모범 사례를 제공하는 것을 목표로 합니다.  

### 대화형 컴포넌트

모달 대화상자, 드롭다운 메뉴와 맞춤 툴팁과 같은 부트스트랩 대화형 컴포넌트는 터치, 마우스 및 키보드 사용자들 위해 설계되었습니다. 이와 관련된 [<abbr title="웹 접근성 계획">WAI</abbr>-<abbr title="접근가능한 리치 인터넷 응용 프로그램">ARIA</abbr>](https://www.w3.org/WAI/intro/aria) 역할과 속성의 사용을 통해, 컴포넌트들은 보조 기술을 사용하여 정상적이며 작동할수 있어야 합니다.  

부트스트랩의 컴포넌트는 의도적으로 상당히 일반적으로 사용할 수 있도록 설계되었으므로, 작성자는 컴포넌트의 특성과 기능성을 정확히 전달하기 위해서는 자바스크립트 동작뿐만 아니라 <abbr title="Accessible Rich Internet Applications">ARIA</abbr> 역할과 속성을 더 깊이 포함하는 것이 필요할 것입니다. 이것은 보통 설명서에 명시되어 있습니다.

### 색상 대비

버튼 변형, 알림 변형, 폼 유효성 검사 표시자 등 프레임워크 전반에 걸쳐 현재 부트스트랩의 기본 팔레트를 구성하는 대부분의 색상은 밝은 배경에서 사용될 때 *불충분한* 색상 대비 (권장되는 [WCAG 2.0 색상 대비 4.5:1 비율](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) 미만) 로 이어집니다. 작성자는 적절한 색상 대비 비율을 보장하기 위해 기본 색상을 수동으로 수정/확장해야 합니다.

### 시각적으로 숨겨진 콘텐츠

시각적으로 숨겨져 있어야 하지만 스크린 리더같은 보조 기술에서 접근할 수 있어야 하는 콘텐츠는 `.sr-only` 클래스를 사용하여 스타일을 지정할 수 있습니다. 이는 시각적이지 않은 사용자에게 추가적인 시각적 정보 또는 신호 (예: 색상 사용으로 표시된 의미) 를 전달해야 하는 상황에서 유용할 수 있습니다.

{% highlight html %}
<p class="text-danger">
  <span class="sr-only">위험: </span>
  이 동작은 되돌릴 수 없습니다.
</p>
{% endhighlight %}

전통적인 "건너 뛰기" 링크와 같이 시각적으로 숨겨진 대화형 컨트롤의 경우 `.sr-only` 는 `.sr-only-focusable` 클래스와 결합될 수 있습니다. 이렇게 하면 컨트롤이 포커스된 상태에서는 보이도록 합니다 (시각이 있는 키보드 사용자들을 위해)

{% highlight html %}
<a class="sr-only sr-only-focusable" href="#content">주요 콘텐츠로 건너 뛰기</a>
{% endhighlight %}

### 축소된 모션

부트스트랩에는 [`prefers-reduced-motion` 미디어 기능](https://drafts.csswg.org/mediaqueries-5/#prefers-reduced-motion) 에 대한 지원이 포함됩니다. 사용자가 축소된 모션에 대한 환경설정을 지정할 수 있는 브라우저/환경에서, 부트스트랩의 대부분의 CSS 전환 효과 (예를 들면 모달 대화 상자를 열거나 닫을때)가 비활성화됩니다. 현재, 맥OS 나 iOS 에서는 사파리로만 지원이 제한됩니다.

## 추가 리소스

- [Web Content Accessibility Guidelines (WCAG) 2.0](https://www.w3.org/TR/WCAG20/)
- [The A11Y Project](http://a11yproject.com/)
- [MDN accessibility documentation](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
- [Tenon.io Accessibility Checker](https://tenon.io/)
- [Colour Contrast Analyser (CCA)](https://developer.paciellogroup.com/resources/contrastanalyser/)
- ["HTML Codesniffer" bookmarklet for identifying accessibility issues](https://github.com/squizlabs/HTML_CodeSniffer)
