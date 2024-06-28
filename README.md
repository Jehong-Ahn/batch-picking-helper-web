## Eleventy + Pug 를 사용하는 이유

Pug는 가장 심플하게 html을 작성할 수 있는 템플릿인데, 이것만으로는 사이트 전체를 만들기 어렵다.

express에 연동하더라도, 각 페이지마다 route를 설정하건, dynamic route logic을 작성해야 하고

빌드하여 html 파일로 저장하는 기능도 없다. 

eleventy가 있으면 이 모든 것이 바로 된다. 

## Eleventy 프로젝트에 Pug 연동 방법

먼저 `pug`를 설치하고,

`.eleventy.js`의 `setTemplateFormats()`에 pug를 추가한다. 이것만으로 pug 연동은 끝난다.


## Glitch 프로젝트와 HTML 빌드

`watch.json`은 glitch에서 preview live reload를 위해 사용하는 설정이다. `restart.exclude`에 pug를 추가한다. 레이블명이 왜 저런지는 나도 모른다.

glitch project 오픈 시, `npm run start`가 실행되어 `eleventy --serve`가 시작된다. 이로써, 아무 파일이나 수정할때마다 모든 파일이 다시 빌드된다.

빌드된 html 파일들은 `build/` 경로에 저장된다. 이를 파일트리에서 보고 싶으면 `.gitignore`에서 제거한다.

빌드된 html 파일들이 http serve된다. node app이 아니다. 이는 `package.json`에 `glitch` 설정이 되어 있기 때문이다.

에디터 사용 중에 빌드된 파일들은 dev mode이다. prod mode으로 빌드하려면 `npm run build`한다.


## 빌드 경로 변경

github pages 연동하려면 docs 에 빌드해야 한다. (action 사용하면 상관없기는 하다.)

`.eleventy.js`에서 output 변경하고

`package.json`에 buildPath 설정한다.


## Pug 사용법

`extends`에 _includes/에 대해 참고 가능

레이아웃에 데이터를 패스하는 방법은 기존 md와 같다.

레이아웃에서 데이터를 interpolation하는 방법은 pug 문서에 나온대로 하면 된다.

