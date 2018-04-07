---
layout: docs
title: Webpack
description: Webpack 3 을 이용하여 프로젝트에 부트스트랩을 포함하는 방법을 배워보세요.
group: getting-started
toc: true
---

## 부트스트랩 설치

npm 을 사용하여 Node.js 모듈로 [부트스트랩을 설치합니다]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/download/#npm) 


## 자바스크립트 가져오기

앱의 진입점 (보통 `index.js` 나 `app.js`) 에 다음 코드를 추가하여 [부트스트랩의 자바스크립트]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/javascript/) 을 가져옵니다.

{% highlight js %}
import 'bootstrap';
{% endhighlight %}

또는, 필요에 따라 **플러그인을 개별적으로 가져올 수도 있습니다.**

{% highlight js %}
import 'bootstrap/js/dist/util';
import 'bootstrap/js/dist/dropdown';
...
{% endhighlight %}

부트스트랩은 [jQuery](https://jquery.com/) 와 [Popper](https://popper.js.org/) 에 의존하며, 
이것들은 `peerDependencies` 으로 정의됩니다. 이것은 당신이 `npm install --save jquery popper.js` 을 사용하여
`package.json` 에 그것들 모두를 추가해야 한다는 것을 의미합니다.

{% capture callout %}
**플러그인을 개별적으로 가져오는 것** 을 선택했다면, [exports-loader](https://github.com/webpack-contrib/exports-loader) 도 설치해야합니다.
{% endcapture %}
{% include callout.html content=callout type="warning" %}

## 스타일 가져오기

### 미리 컴파일된 Sass 가져오기

부트스트랩의 잠재력을 즐기고 필요에 맞게 맞춤화하려면, 당신의 프로젝트의 번들링 프로세스의 일부로 소스 파일들을 이용하세요

먼저, 자신만의 `_custom.scss` 파일을 만들고 [내장된 맞춤화 변수]({{ site.baseurl }}/docs/{{ site.docs_version }}/getting-started/options/) 를 오버라이드 하는데 사용합니다. 그런 다음, 맞춤 변수를 메인 Sass 파일에 가져오고, 그 다음에 부트스트랩이 오도록 하세요.

{% highlight scss %}
@import "custom";
@import "~bootstrap/scss/bootstrap";
{% endhighlight %}

부트스트랩을 컴파일하려면, 필수 로더 ([sass-loader](https://github.com/webpack-contrib/sass-loader), [Autoprefixer](https://github.com/postcss/autoprefixer#webpack) 을 사용하는 [postcss-loader](https://github.com/postcss/postcss-loader)) 들을 설치하고 사용해야합니다. 최소한의 설정으로 webpack 설정에는 다음과 비슷한 규칙이 포함되어 있어야 합니다.

{% highlight js %}
  ...
  {
    test: /\.(scss)$/,
    use: [{
      loader: 'style-loader', // 페이지에 CSS 를 삽입
    }, {
      loader: 'css-loader', // CSS 를 CommonJS 모듈로 변환
    }, {
      loader: 'postcss-loader', // post css 동작을 실행
      options: {
        plugins: function () { // post css 플러그인은 postcss.config.js 로 내보낼 수 있습니다.
          return [
            require('precss'),
            require('autoprefixer')
          ];
        }
      }
    }, {
      loader: 'sass-loader' // compiles Sass to CSS
    }]
  },
  ...
{% endhighlight %}

### 컴파일된 CSS 가져오기

또는 프로젝트 진입점에 다음 코드를 추가하여 부트스트랩의 CSS 를 바로 사용할 수도 있습니다.

{% highlight js %}
import 'bootstrap/dist/css/bootstrap.min.css';
{% endhighlight %}

이 경우에 `sass-loader` 가 필요하지 않다는 점을 제외하면 특별히 수정하지 않고 `css` 에 대해 기존 규칙을 사용할 수 있습니다. 그냥 [style-loader](https://github.com/webpack-contrib/style-loader) 과 [css-loader](https://github.com/webpack-contrib/css-loader) 을 사용하세요.

{% highlight js %}
  ...
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      }
    ]
  }
  ...
{% endhighlight %}
