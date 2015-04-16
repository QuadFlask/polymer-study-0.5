# polymer-study-0.5

## ~#8 까지 배운것

### 프로젝트 설정

`bower init` 으로 현재 디렉터리에 프로젝트를 만든다.

`bower install --save Polymer/polymer`, `bower install --save Polymer/platform` 로 폴리머 다운로드

> 이 튜토리얼에선 0.5버전이라서 0.8과 호환 안됨. 특히 polymer-element 로 커스텀 엘리먼트를 만드는 태그가 없어졌다. 이것때문에 하루 놈

`python -m SimpleHTTPServer` 로 로컬 서버 띄우기 사용(파이썬 버전 2.x, 3.x 마다 명령어가 다르다.)

index.html 에서 폴리머를 사용하기 위해선 

```html
<script src="bower_components/platform/platform.js"></script>
```

로 스크립트를 로드해야 함.

### 커스텀 앨리먼트 만들기 

```html
<link rel="import" href="bower_components/polymer/polymer.html">
```
를 로드한뒤, 

```html
<polymer-element name="test-elem" attributes="name">
<template>
	<style>
		h1{
			font-family: sans-serif;
			text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
		}
	</style>
	<h1>Hello {{name}}</h1>
	<input type="text" value="{{name}}">
	<button on-click="{{changeName}}">Change Name</button>
</template>
<script>
	Polymer('test-elem', {
		ready: function(){
			this.name = "world";
		},
		changeName: function(){
			this.name = "You";
		}
	})
</script>
</polymer-element>
```

이런식으로 만들어 주면 됨.

여기서 스크립트가 필요 없을경우, `polymer-element` 태그에 noscript 애트리뷰트를 넣어줘야함.

기본적으로 AngularJS 와 비슷하게 2-way data binding 을 지원하며 $scope 대신 그냥 this 에 할당하면 된다.

그리고 앨리먼트가 레디 됬을 때 이벤트로 `ready`를 정의해서 초기화 해주면 되고, 리스트 리핏또한 비슷하다.(단지 curly brace 가 들어간다는것 빼곤.)


> 0.8 버전에선 달라졌는데 일단은 0.5 버전 기준으로 공부한뒤, 마이그레이션 하자

### core-element 사용하기

폴리머에서 사용할 수 있도록 미리 만들어진 녀석들이 있는데 설치해줘야함.

`bower install --save Polymer/core-elements`로 현재 디렉터리에 다운 받은뒤, 

```html
<script src="bower_components/webcomponentsjs/webcomponents.js"></script>
```

로 로드하고,

```html
<link rel="import" href="bower_components/core-tooltip/core-tooltip.html">
```

로 사용하고자 하는 컴포넌트를 로드한다.



[http://leveluptuts.com/tutorials/polymer-tutorials/9-core-layout-elements-part-1](http://leveluptuts.com/tutorials/polymer-tutorials/9-core-layout-elements-part-1)
