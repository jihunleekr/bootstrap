---
layout: docs
title: 레이아웃 유틸리티
description: 모바일 친화적이고 반응형 개발을 빠르게 하기 위해, 부트스트랩은 콘텐츠의 보이기, 숨기기, 정렬하기, 간격조절을 위한 수십 가지 유틸리티 클래스들을 포함하고 있습니다.
group: layout
toc: true
---

## `display` 변경

`display` 속성의 일반값을 적절하게 변경하기 위해 [display 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/display/) 를 사용하세요.
그리드 시스템, 콘텐츠, 컴포넌트와 섞어 특정한 뷰포트에서 그것들을 표시하거나 숨깁니다.

## Flexbox 옵션

부트스트랩 4 는 flexbox 로 만들어졌지만, 모든 요소의 `display` 가 `display: flex` 로 변경된 것은 아니기 떄문에 불필요한 오버라이드가 추가되고 예기치 않게 주요 브라우저 동작이 변경될 수 있습니다. 대부분의 [컴포넌트]({{ site.baseurl }}/docs/{{ site.docs_version }}/components/alerts/) 는 flexbox 를 사용하여 만들어집니다. 

요소에 `display: flex` 를 추가해야 한다면, `.d-flex` 또는 반응형 변형 (예: `.d-sm-flex`) 중 하나를 사용하세요. 크기조정, 정렬, 간격조정 등을 위해서 이 클래스 또는 `display` 값을 변경하기 위한 [flexbox 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/flex/) 가 필요할 것입니다.

## 여백과 패딩

요소와 컴포넌트들이 간격과 크기를 조정할 방법을 제어하기 위해 `margin` 과 `padding` [spacing 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/spacing/) 를 사용하세요. 부트스트랩 4 는 `$spacer` 변수 기본값 `1rem` 를 기반으로 5 단계 spacing 유틸리티가 포함되어 있습니다. 모든 뷰포트 (예: `margin-right: 1rem` 의 경우 `.mr-3`), 혹은 특정한 뷰포트 (예: `md` 중단점부터 `margin-right: 1rem` 의 경우 `.mr-md-3`) 를 대상으로 하는 반응형을 선택하세요.

## `visibility` 전환

`display` 를 전환할 필요가 없는 경우, [visibility 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/visibility/) 로 요소의 `visibility` 를 전환할 수 있습니다. 보이지 않는 요소는 페이지의 레이아웃에 영향을 미치지만, 방문자에게 시각적으로 숨겨집니다.
