---
layout: docs
title: 다운로드
description: 컴파일된 CSS, 자바스크립트, 소스코드 등을 얻기위해 부트스트랩을 다운로드 하거나 npm, RubyGems 등과 같은 선호하는 패키지 매니저로 포함 시키세요.
group: getting-started
toc: true
---

## 컴파일된 CSS and JS

프로젝트에 쉽게 추가하여 바로 사용 가능한 컴파일된 코드를 다운로드 하세요. 다음을 포함합니다.

- 컴파일되고 압축된 CSS 묶음 ([CSS files comparison]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/contents/#comparison-of-css-files) 참고)
- 컴파일되고 압축된 자바스크립트 플러그인

이것은 설명서, 소스파일, 부가적인 자바스크립트 의존성(jQuery 와 Popper.js)을 포함하지 않습니다.

<a href="{{ site.download.dist }}" class="btn btn-bd-primary" onclick="ga('send', 'event', 'Getting started', 'Download', 'Download Bootstrap');">다운로드</a>

## 소스파일

Sass, 자바스크립트, 설명서 소스 파일을 다운로드하여 자신만의 자산 파이프라인으로 부트스트랩을 컴파일하세요. 이 옵션은 몇가지 추가 도구가 필요합니다.

- CSS 를 컴파일하기 위한 Sass 컴파일러 (Libsass 또는 Ruby Sass 가 지원됨).
- 브라우저 업체별 CSS 접두어를 위한 [Autoprefixer](https://github.com/postcss/autoprefixer) 

[빌드 도구]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/build-tools/#tooling-setup)가 필요하다면, 부트스트랩과 설명서를 개발하기 위해 포함되어 있습니다만, 당신의 목적에 아마 적합하지 않을 것입니다.

<a href="{{ site.download.source }}" class="btn btn-bd-primary" onclick="ga('send', 'event', 'Getting started', 'Download', 'Download source');">소스 다운로드</a>

## 부트스트랩 CDN

당신의 프로젝트에 부트스트랩의 컴파일된 CSS 와 JS 의 캐시된 버전을 전달하기 위해 [부트스트랩 CDN](https://www.bootstrapcdn.com/) 으로 다운로드를 건너뛸 수 있습니다.

{% highlight html %}
<link rel="stylesheet" href="{{ site.cdn.css }}" integrity="{{ site.cdn.css_hash }}" crossorigin="anonymous">
<script src="{{ site.cdn.js }}" integrity="{{ site.cdn.js_hash }}" crossorigin="anonymous"></script>
{% endhighlight %}

만약 컴파일된 자바스크립트를 사용한다면, 그전에 jQuery 와 Popper.js 의 CDN 버전을 포함하는 것을 잊지 마세요.

{% highlight html %}
<script src="{{ site.cdn.jquery }}" integrity="{{ site.cdn.jquery_hash }}" crossorigin="anonymous"></script>
<script src="{{ site.cdn.popper }}" integrity="{{ site.cdn.popper_hash }}" crossorigin="anonymous"></script>
{% endhighlight %}

## 패키지 관리자

가장 많이 쓰이는 몇몇의 패키지 관리자로 대부분의 프로젝트에 부트스트랩의 **소스 파일** 을 가져오세요. 패키지 관리자는 뭐든지 상관없습니다. 부트스트랩은 공식 컴파일된 버전과 맞는 설정을 위해 **Sass 컴파일러와 [Autoprefixer](https://github.com/postcss/autoprefixer)** 가 필요합니다. 

### npm

[npm 패키지](https://www.npmjs.com/package/bootstrap) 로 Node.js 구동 앱에 부트스트랩을 설치하세요.

{% highlight sh %}
npm install bootstrap
{% endhighlight %}

`require('bootstrap')` 은 jQuery 개체에 부트스트랩의 모든 jQuery 플러그인을 불러올 것입니다. `bootstrap` 모듈은 스스로 어떤 것도 export 하지 않습니다. 패키지의 최상위 디렉토리 아래 `/js/*.js` 파일들을 수동으로 불러와서 부트스트랩의 jQuery 플러그인들을 개별적으로 불러올 수 있습니다.

부트스트랩의 `package.json` 는 다음의 키에 몇몇 추가적인 메타데이터를 포함합니다.

- `sass` - 부트스트랩의 메인 [Sass](http://sass-lang.com/) 소스 파일 경로
- `style` - 부트스트랩의 기본 설정(맞춤 설정을 사용하지 않음)을 사용하여 미리 컴파일되고 압축되지는 않은 CSS 의 경로

### RubyGems

[`Gemfile`](https://bundler.io/gemfile.html) 에 다음의 코드를 추가하여 [Bundler](https://bundler.io/) (**추천함**) 와 [RubyGems](https://rubygems.org/) 를 이용하여 루비앱에 부트스트랩을 설치하세요.

{% highlight ruby %}
gem 'bootstrap', '~> {{ site.current_ruby_version }}'
{% endhighlight %}

만약 Bundler 를 사용하지 않는다면, 다음의 명령어를 실행하여 설치할 수 있습니다.

{% highlight sh %}
gem install bootstrap -v {{ site.current_ruby_version }}
{% endhighlight %}

자세한 사항은 [gem 의 README 를 보세요](https://github.com/twbs/bootstrap-rubygem/blob/master/README.md).

### Composer

또한 [Composer](https://getcomposer.org/) 를 이용하여 부트스트랩의 Sass 와 자바스크립트를 설치하고 관리할 수 있습니다.

{% highlight sh %}
composer require twbs/bootstrap:{{ site.current_version }}
{% endhighlight %}

### NuGet

만약 .NET 에서 개발하고 있다면, [NuGet](https://www.nuget.org/) 을 이용하여 부트스트랩의 [CSS](https://www.nuget.org/packages/bootstrap/) 나 [Sass](https://www.nuget.org/packages/bootstrap.sass/) 와 자바스크립트를 설치하고 관리할 수 있습니다.

{% highlight powershell %}
Install-Package bootstrap
{% endhighlight %}

{% highlight powershell %}
Install-Package bootstrap.sass
{% endhighlight %}
