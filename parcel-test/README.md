#
## Javascript Bundler
#

>자바스크립트에서 사용하는 여러가지 라이브러리들이 웹에서 동작할 수 있도록 변환 해주는 역할을 한다. 번들러 자체가 모든 것들을 바꿔 주는 것은 아니다 예를들어 Scss를 사용한다 했을때 scss 문법을 번들러 자체가 이해하고 있어서 변환해 주는 것이 아니다 다만 sass의 패키지에게 컴파일을 시키는 것을 우리는 번들러에게 위임하는 것이다. 번들러는 해당 패키지의 도움을 받아 파일을 변환한다.   
대표적으로 Parcel ,Webpack ,Rollup가 있다 .


#
### Parcel vs Webpack
#

Parcle | Webpack
--|--
구성없는 단순한 자동 번들링 | 매우 꼼꼼한 구성
소/중형 프로젝트에 적합 | 중/대형 프로젝트에 적합



#
## Parcel 
#

>정적 파일 연결

```js
//parcel-plugin-static-files-copy의 도움을 받아 정적폴더를 지정하고 
//build시에 정적파일들을 dist폴더로 넘겨 줄 수 있다.
//npm 으로 인스톨하고
npm i parcel-plugin-static-files-copy

//package.json에서 아래와 같이 설정한다.
//staticPath에 속한 파일들은 컴파일시 dist 폴더에 추가된다.
{
	...
    "staticFiles": {
        //정적 폴더지정  
        "staticPath": "정적폴더명",
    }
}

```
>아래 링크에 사용법이 자세히 나와있다.
https://www.npmjs.com/package/parcel-plugin-static-files-copy


#
### postcss , autoprefixer
#
>vendor prefix를 자동으로 제공하는 라이브러리
    
    //postcss,autoprefixer install   

    npm i -D postcss autoprefixer
```js
//autoprefixer 패키지 설정을 위한 package.json 속성
{
    "browserslist":[
        //점유율 1퍼센트 이상의 브라우저
        ">1%",
        //마지막 2개 버전까지 지원
        "last 2 versions"
    ]
}
```


#
### Babel
#

> 바벨은 ECMAScript 2015 + 코드를 이전 Javascript 엔진에서 실행할 수 있는 이전 버전과 호환되는 javascript 버전으로 변환하는 데 주로 사용되는 무료 오픈 소스 Javascript 트랜스 컴파일러이다(참조 위키백과)   

```js
//루트 경로에.babelrc.js 파일을 만들어 아래 코드를 추가하면 바벨이 사용된다.
//.babelrc.js 에서 rc는 설정파일을 의미한다.
//작성하는 모든 자바스크립트는 바벨을 통해서 ES5로 변경되서 나간다.
//babel도 package.json의 "browserslist"의 영향을 받는다. 
module.exports = {
    presets: ['@babel/preset-env'] 
}
```
