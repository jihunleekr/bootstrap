---
layout: docs
title: 코드
description: 부트스트랩에서 인라인 및 여러줄 블록 보여주기 위한 설명서와 예제.
group: content
toc: true
---

## 인라인 코드

`<code>` 으로 인라인 코드조각을 감싸세요. HTML 꺽쇠 괄호를 이스케이프 하는 것을 명심하세요.

{% capture example %}
예를 들어, <code>&lt;section&gt;</code> 은 인라인으로 감싸져야 합니다.
{% endcapture %}
{% include example.html content=example %}

## 코드 블록

여러줄의 코드에는 `<pre>` 를 사용하세요. 다시 한번 얘기하자면 적절한 렌더링을 위해서 코드 내의 꺽쇠 괄호는 이스케이프해야합니다. `.pre-scrollable` 클래스를 추가하여, 340px 으로 최대 높이를 설정하고 y 축 스크롤바를 제공할 수도 있습니다.

{% capture example %}
<pre><code>&lt;p&gt;Sample text here...&lt;/p&gt;
&lt;p&gt;And another line of sample text here...&lt;/p&gt;
</code></pre>
{% endcapture %}
{% include example.html content=example %}

## 변수

변수를 표시하기 위해서 `<var>` 태그를 사용하세요.

{% capture example %}
<var>y</var> = <var>m</var><var>x</var> + <var>b</var>
{% endcapture %}
{% include example.html content=example %}

## 사용자 입력

키보드를 통해서 일반적으로 들어오는 입력을 표시하려면 `<kbd>` 를 사용하세요.

{% capture example %}
To switch directories, type <kbd>cd</kbd> followed by the name of the directory.<br>
To edit settings, press <kbd><kbd>ctrl</kbd> + <kbd>,</kbd></kbd>
{% endcapture %}
{% include example.html content=example %}

## 예제 출력

프로그램의 예제 출력을 표시하려면 `<samp>` 태그를 사용하세요.

{% capture example %}
<samp>This text is meant to be treated as sample output from a computer program.</samp>
{% endcapture %}
{% include example.html content=example %}
