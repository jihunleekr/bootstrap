---
layout: docs
title: Figures
description: 부트스트랩에서 figure 컴포넌트로 관련된 이미지와 텍스트를 표시하는 설명서와 예제
group: content
---

캡션이 있는 이미지와 같은 콘텐츠를 표시해야하는 경우, `<figure>` 를 사용하는 것을 고려해보세요.

내장된 `.figure` , `.figure-img`, `.figure-caption` 클래스를 사용하여 HTML5 `<figure>` 와 `<figcaption>` 요소에 대한 기본 스타일을 제공하세요. figure 내 이미지는 명확한 사이즈가 없으므로 반응형을 만들기 위해 `<img>` 에 `.img-fluid` 클래스를 추가하도록 하세요.

{% capture example %}
<figure class="figure">
  <img data-src="holder.js/400x300" class="figure-img img-fluid rounded" alt="A generic square placeholder image with rounded corners in a figure.">
  <figcaption class="figure-caption">A caption for the above image.</figcaption>
</figure>
{% endcapture %}
{% include example.html content=example %}

[텍스트 유틸리티]({{ site.baseurl }}/docs/{{ site.docs_version }}/utilities/text/#text-alignment) 를 사용하여 figure 캡션을 쉽게 정렬하세요.

{% capture example %}
<figure class="figure">
  <img data-src="holder.js/400x300" class="figure-img img-fluid rounded" alt="A generic square placeholder image with rounded corners in a figure.">
  <figcaption class="figure-caption text-right">A caption for the above image.</figcaption>
</figure>
{% endcapture %}
{% include example.html content=example %}
