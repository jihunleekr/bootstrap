---
layout: docs
title: 빌드 도구
description: 부트스트랩에 포함된 npm 스크립트를 사용하여 설명서를 작성하고, 소스 코드를 컴파일하고, 테스트를 실행하는 방법 등에 대해 배웁니다.
group: getting-started
toc: true
---

## 툴 설정

부트스트랩은 빌드 시스템에 [NPM scripts](https://docs.npmjs.com/misc/scripts) 를 사용합니다. 우리의 [package.json]({{ site.repo }}/blob/v{{ site.current_version }}/package.json) 에는 코드 컴파일, 테스트 실행 등 프레임워크 작업을 위한 편리한 방법이 포함되어 있습니다.

빌드 시스템을 사용하고 설명서를 로컬에서 실행하려면 부트 스트랩의 소스 파일과 Node 를 복사하는 것이 필요합니다. 다음 단계를 따라 준비가 되어 있어야 합니다.

1. 의존성을 관리하는데 사용되는 [Node.js 를 다운로드하고 설치합니다](https://nodejs.org/download/)
2. 루트 `/bootstrap` 디렉토리로 이동하여 `npm install` 을 실행하여 [package.json]({{ site.repo }}/blob/v{{ site.current_version }}/package.json) 에 나열된 로컬 의존성을 설치합니다.
3. [Ruby 를 설치][install-ruby], `gem install bundler` 로 [Bundler][gembundler] 를 설치, 그리고 마지막으로 `bundle install` 을 실행합니다. 이것은 Jekyll 과 플러그인과 같은 Ruby 의 의존성을 설치합니다.
  - **윈도우즈 사용자:** [이 가이드](https://jekyllrb.com/docs/windows/) 를 읽어서 문제 없이 Jekyll 를 실행하세요.  

완료되면, 명령줄에서 제공되는 다양한 명령을 실행할 수 있습니다.

[install-ruby]: https://www.ruby-lang.org/en/documentation/installation/
[gembundler]: https://bundler.io/

## NPM 스크립트 사용

우리의 [package.json]({{ site.repo }}/blob/v{{ site.current_version }}/package.json) 에는 다음과 같은 명령어와 작업이 포함되어 있습니다.

| 작업 | 설명 |
| --- | --- |
| `npm run dist` | `npm run dist` 는 컴파일된 파일들로 `/dist` 디렉토리를 생성합니다. **[Sass](http://sass-lang.com/), [Autoprefixer][autoprefixer], [UglifyJS](https://github.com/mishoo/UglifyJS2) 을 사용합니다.** |
| `npm test` | `npm run dist` 와 동일하며 로컬에서 테스트를 실행합니다 |
| `npm run docs` | 설명서를 위한 CSS 와 자바스크립트를 빌드하고 lint 합니다. 그다음 `npm run docs-serve` 를 통해 설명서를 로컬에서 실행할 수 있습니다. |

모든 npm 스크립트를 보려면 `npm run` 을 실행하세요.

## Autoprefixer

부트스트랩은 [Autoprefixer][autoprefixer] (빌드 프로세스에 포함됨) 을 사용하여 빌드시 일부 CSS 속성에 접두어를 자동으로 추가합니다. 이렇게 하는 것은 v3 에서 있었던 벤더 믹스인의 필요성을 없에고 CSS 핵심 부분을 한번에 작성할 수 있으므로 시간과 코드를 절약할 수 있습니다. 

Autoprefixer 를 통해 지원되는 브라우저 목록은 깃허브 저장소의 별도 파일에 보관됩니다. 자세한 내용은 [/package.json]({{ site.repo }}/blob/v{{ site.current_version }}/package.json) 을 참조하세요.

## 로컬 설명서

로컬에서 문서를 실행하려면 Jekyll 의 사용이 필요합니다. Jekyll 은 기본적인 포함, 마크다운 기반 파일, 템플릿 등을 제공하는 유연한 정적 사이트 생성기입니다. 그것을 시작하는 방법은 다음과 같습니다.

1. 위의 [툴 설정](#tooling-setup) 을 통해 실행하여, Jekyll (사이트 빌더) 과 다른 Ruby 의존성을 `bundle install` 로 설치하세요.
2. 루트 `/bootstrap` 디렉토리에서, 명령줄에서`npm run docs-serve` 를 실행하세요.
3. 브라우저에서 `http://localhost:9001` 을 엽니다.

[Jekyll 설명서](https://jekyllrb.com/docs/home/) 를 읽어 그것을 사용하는 법을 배워보세요.

## 문제해결

의존성을 설치하는데 문제가 생겼다면 이전 의존성 버전을 제거하고 (전역과 로컬), 다시 `npm install` 을 실행해보세요.

[autoprefixer]: https://github.com/postcss/autoprefixer
