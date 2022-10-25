[Sevelt and Sapper in Action by Mark Volkmann, 2020]()

# Part 1. 시작하기
# Chapter 1. 선수 입장
## 1.1 스벨트란
스벨트는 프랑스어로 **‘늘씬하다’**는 뜻이다.

Rich Harris가 만들었다.

### 1.1.1 스벨트를 써야 하는 이유

#### 스벨트는 컴파일러다
리액트와 같은 런타임 라이브러리가 아니라 **타입 스크립트로 만든** 웹 애플리케이션 **컴파일러**이다.

**스벨트의 UI 컴포넌트**는 .svelte 파일에 정의합니다.
스벨트 컴파일러는 **.svelte 파일을 HTML, CSS, JavaScript로 컴파일**한다.

#### 스벨트로 만드는 번들은 다른 웹 프레임워크들 보다 작다

#### 스벨트는 코드를 적게 사용한다

#### 스벨트는 Virtual DOM 없이 반응성을 제공한다
**반응성**은 애플리케이션이나 컴포넌트의 상태 변경에 따라서 DOM을 업데이트하는 것을 뜻한다. 스벨트는 컴포넌트를 화면에 그리는 것에 영향을 줄 수 있는 최상위 수준 컴포넌트 변수가 변경되는지 추적한다. 함수 내부에만 있는 변수는 추적하지 않는다. 그리고 값이 변경되면, 전체 컴포넌트가 아닌 영향을 받는 부분에 포함되는 DOM만 업데이트한다.

#### 스벨트는 빠르다

#### 스벨트는 메모리를 덜 차지한다

#### 스벨트 컴포넌트는 자바 스크립트 컨테이너를 쓰지 않는다
.svelte 파일은 컴포넌트를 정의할 때 어떤 형태로든 JavaScript 함수나 객체 등을 쓰지 않는다. 대신 HTML, style, script 요소를 조합해서 컴포넌트를 만든다.

#### 스벨트에서 스타일은 유효 범위를 가진다
기본적으로 스벨트 컴포넌트에서의 CSS는 해당 컴포넌트 내에서만 유효하다.

#### 스벨트는 전역 스타일을 지정할 수 있다
Public/global.css에 스타일을 정의하면 모든 컴포넌트 스타일에 영향을 줄 수 있다.

#### 스벨트는 단순한 상태 관리 기법을 제공한다

#### 스벨트는 양방향 데이터 바인딩을 제공한다
스벨트는 input, texture, select 와 같은 폼 제어 값과 컴포넌트 변수를 쉽게 묶을 수 있도록 한다.

#### 스벨트에서는 애니메이션을 쉽게 만들 수 있다

#### 스벨트는 다양한 접근성을 권장한다
스벨트는 런타임 동안 다양한 접근성 문제에 대한 경고를 표시해준다.
스벨트는 접근성을 제공하는 부분이 제대로 설정되지 않으면 콘솔에 경고를 표시하여 개발자가 다양한 접근성에 신경 쓰도록 한다.

### 1.1.2 반응성에 대한 고찰
앱 애플리케이션에서 **반응성(reactivity)**이란 데이터 또는 상태가 변경될 때 이에 따라 자동으로 DOM이 변경되는 것을 의미한다.

#### HTML DOM
HTML DOM은 **웹 페이지에 대한 메모리 표현 방식**이다.
HTML DOM은 트리 형태의 JavaScript 객체로 구성되며, 각 객체는 트리의 노드가 된다.

#### Rethinking Reactivity
[https://www.youtube.com/watch?v=gJ2P6hGwcgo][2]
1. 스프레드시트를 만들 듯 ‘반응성 프로그래밍’을 해라. 값이 바뀌면, 그 결과로 다른 값이 바뀔 수 있다.
2. Virtual DOM 사용을 피하라. “엔지니어로서 비효율적인 것은 불쾌하게 생각해야 한다.”
3. 코드를 적게 써라. 개발자에게도, 성능에도 모두 바람직한 일이다. “코드의 속도를 향상시킬 수 있는 유일하게 믿을 수 있는 방법은 코드를 없애는 것이다.”
4. 접근성 문제에 대한 경고를 표시해야 한다.
5. 스타일은 해당 컴포넌트에만 국한시켜야 하며, 의도치 않게 새어나가서 다른 컴포넌트에 영향을 주는 일은 없어야 한다.
6. 사용되지 않는 CSS 규칙을 찾아내고 제거할 수 있어야 한다.
7. 변환이나 애니메이션을 쉽게 추가할 수 있어야 한다. 물론 좋은 성능을 위해서 CSS를 써야 한다.
8. 프레임워크 기능을 쓰기 위해서 쓰지도 않는 기능을 애플리케이션에 포함하는 경우는 없어야 한다.
9. 페이지 라우팅이나 코드 분할, 서버 사이드 렌더링 등의 기능을 쓰고 싶다면 새퍼를 써라.
10. 모바일 앱을 만들어야 한다면 스벨트 네이티브를 써라. 리액트 네이티브를 대신 할 수 있다.

### 1.1.3 현재까지 알려진 스벨트의 이슈들

### 1.1.4 스벨트는 어떻게 동작하는가
스벨트 컴파일러는 .svelte 파일을 하나의 bundle.js와 하나의 bundle.css 파일로 만든다. 각각은 오직 JavaScript와 CSS만 담고 있다.

모든 컴포넌트에 영향을 미칠 수 있는 전역 스타일은 global.css 파일에 정의된다. 메인 HTML 파일인 index.html은 global.css 파일과 bundle.css, bundle.js 파일을 임포트한다. 그리고 웹 브라우저는 이 HTML 파일을 불러와서 애플리케이션을 실행한다.

스벨트 컴파일러는 bundle.css.map과 bundle.js.map 파일도 생성한다. 이 파일들은 원래의 소스 코드와 생성된 코드 사이의 매핑을 제공한다. 그래서 이 파일들은 브라우저 내장 디버거 등에서 사용된다.

### 1.1.5 그럼 스벨트가 사라지는 걸까
스벨트 컴파일러가 번들을 만들 때 스벨트 라이브러리는 포함시키지 않는다. 그러나 스벨트 라이브러리의 코드 일부는 배포에 포함된다.

스벨트 라이브러리는 node\_modules/svelte 디렉토리에 internal.js 파일로 정의되어 있다. 그 외 easing.js, motion.js, register.js, store.js, transition.js와 같이 특정 기능을 지원하기 위해 정의된 파일들이 있다.

스벨트 라이브러리 코드가 배포에 포함되지 않는 것은 아니다. 다만 다른 앱 프레임워크 보다 아주 적을 뿐이다.

## 1.2 새퍼란
새퍼(Sapper)는 스벨트 기반 프레임워크이다.

새퍼(Sapper)는 ‘Svelte app maker’의 줄임말이고, 영어로 다리를 건설하고 지뢰를 매설하거나 제거하는 ‘공병’을 뜻한다.

### 1.2.1 새퍼를 써야 하는 이유
- 새퍼는 **페이지 라우팅**을 제공한다.  
	페이지 라이팅이란 어떤 URL이 주어졌을 때 애플리케이션이 어떤 페이지를 보여줄지를 정하는 것이다.  
	새퍼에서 페이지 라우팅은 전적으로 디렉토리와 파일의 이름을 짓는 것으로 결정된다.
- 새퍼는 **페이지 레이아웃**을 지원한다.  
	애플리케이션의 여러 페이지가 똑같이 사용하는 페이지를 레이아웃으로 정의할 수 있다.  
	주로 header, footer, nav 영역을 레이아웃으로 정의해서 사용한다.
- 새퍼는 **서버 사이드 렌더링(server-side rendering, SSR)**을 제공한다.  
	서버에서 미리 렌더링한 웹 페이지는 사용자의 웹 브라우저에 JavaScript 코드를 전송하고 실행하는 과정이 없어서 더 나은 사용자 경험을 제공할 수 있다. 또한 검색 엔진 최적화(search engine optimization, SEO)에도 유리하다.  
	새퍼는 세션 내에서 처음 방문하는 페이지에 대해 자동으로 서버 사이드 렌더링을 수행한다.
- 새퍼는 **서버 라우트**를 지원한다.  
	서버 라우트를 통해 웹 애플리케이션 프로젝트 내에서 노드(Node) 기반 API 서비스를 쉽게 만들 수 있다.
- 새퍼는 **코드 분할(code splitting)**을 지원한다.  
	코드 분할은 어떤 페이지를 처음 방문할 때 해당 페이지에 필요한 JavaScript 코드만 다운로드하도록 한다.
- 새퍼는 **프리패치(prefetch)**를 지원한다.  
	프리패치는 사용자가 다른 페이지의 링크 위에 마우스 커서를 올려놓았을 때 해당 페이지를 방문할 것이라 예상하고 페이지 내용을 미리 읽어오는 것을 말한다.  
	페이지에서 필요로 하는 데이터를 읽어오기 위한 API 서비스 요청을 할 수도 있다.
- 새퍼는 **정적 사이트 생성(static site generation)**을 지원한다.  
	정적 사이트 생성은 웹 애플리케이션을 빌드할 때 모든 페이지를 방문해서 HTML로 미리 렌더링 해 둔다.
- 새퍼는 **오프라인 사용**을 지원한다.  
	새퍼는 네트워크 연결이 끊어졌을 때 아주 제한된 용도로 쓸 수 있는 서비스 워커를 사용한다.  
	서비스 워커는 특정 파일이나 서비스 요청에 대한 응답을 캐싱함으로써 네트워크 연결이 끊어졌을 때에도 캐시된 내용을 사용할 수 있도록 해준다.

### 1.2.2 새퍼는 어떻게 동작하는가
새퍼 애플리케이션의 페이지들은 src/routes 디렉토리에 .svelte 파일에 정의된다.  
이 페이지들이 사용하는 컴포넌트들은 src/components 디렉토리에 .svelte 파일에 정의된다.

새퍼 앱은 폴카(Polka) 서버 라이브러리를 기본으로 사용한다.

각 페이지에서 필요로 하는 CSS와 JavaScript 코드는 \_\_sapper\_\_/build/client 디렉토리에 저장한다.  

### 1.2.3 새퍼는 언제 써야 하는가
개발자가 새퍼와는 다른 방식으로 기능을 구현하고 싶다면 그냥 스벨트를 써서 만들 수도 있다. 그러나 아마 대부분의 애플리케이션에서는 새퍼의 기능을 쓰는 것 만으로도 충분할 것이다.

### 1.2.4 이럴 때는 새퍼를 쓰지 마세요
[https://github.com/sveltejs/sapper][3]
새퍼의 버전은 아직 1.0.0이 되지 않았다.

## 1.3 스벨트 네이티브란
[NativeScript][4] 애플리케이션은 사용자 정의 요소를 포함한 XML 문법과 CSS, JavaScript로 만든다. 웹 프레임워크를 쓰지 않아도 되고, 앵귤러, 리액트, 뷰, 스벨트를 쓸 수도 있다.
NativeScript 애플리케이션은 웹 컴포넌트가 아닌 네이티브 컴포넌트를 사용한다.

[SvelteNative][5]는 NativeScript 위에 레이어를 추가한 것이다. 덕분에 나중에 NativeScript의 버전이 바뀌더라도 호환성을 유지할 수 있다.

## 1.4 스벨트와 다른 웹 프레임워크의 차이점
### 1.4.1 앵귤러
### 1.4.2 리액트
### 1.4.3 뷰

## 1.5 어떤 도구로 시작하면 좋을까
스벨트와 새퍼를 사용하려면 최신 버전의 **[Node.js][6]**가 필요하다.
Node.js를 설치하면 터미널에서 node, nom, npc 명령어를 사용할 수 있다.
- node: 앱을 테스트하기 위한 로컬 서버를 실행하거나, 코드 에러 검사, 코드 포맷 지정, 테스트 실행 등의 개발 작업을 할 수 있다.
- nom: 프로젝트에서 사용하는 라이브러리를 설치할 수 있다.
- npx: 새로운 프로젝트를 만들 수 있다.

## 1.6 마치며
- 스벨트는 앱 애플리케이션 개발 도구다.
- 스벨트는 라이브러리가 아니다. 웹 애플리케이션 컴파일러다.
- 스벨트는 코드를 적게 쓰고, 더 작은 크기의 번들을 만들고, 간단한 상태 관리를 제공하는 등의 장점을 가지고 있다.
- 새퍼는 스벨트 기반 도구로 페이지 라우팅, 서버 사이드 렌더링, 코드 분할, 정적 사이트 생성 등의 기능을 제공한다.
- 스벨트 네이티브는 모바일 애플리케이션을 만들 수 있는 도구다.

# Chapter 2. 첫 스벨트 앱 만들기
**REPL**은 **read, evaluate, print, loop**를 의미한다. REPL 도구는 코드를 읽어서\_read\_ 컴파일하거나 에러를 출력하는 등의 평가\_evaluate\_ 작업을 거친 다음 코드의 실행 결과를 출력\_print\_하고 이 과정을 반복\_loop\_한다.

## 2.1 스벨트 REPL
[스벨트 REPL][7] 링크로 이동하면 기본으로 제공하는 ‘Hello World’ 앱이 열린다.

### 2.11. 스벨트 REPL 다루기
REPL은 처음에 **App.svelte** 파일 하나만 제공한다. 하지만 REPL 내의 다른 탭을 써서 다른 파일들을 불러올 수도 있다.

새로 만들어지는 파일은 기본으로 **.svelte** 확장자를 가지지만 파일명을 **.js**로 쓰면 JavaScript 파일이 된다.

스벨트 REPL의 탭
- Result: App.svelte의 출력을 볼 수 있다. console.log와 같은 console 메서드를 사용한 결과도 볼 수 있다.
- JS Output: 스벨트 컴파일러가 생성한 JavaScript 코드를 확인할 수 있다.
- CSS Output: 스벨트 컴파일러가 만든 최소화된 CSS 내용을 볼 수 있다. 사용하지 않는 CSS 셀렉터들은 포함하지 않는다. 모든 셀렉터들은 해당 컴포넌트에만 유효하도록 생성된 CSS 클래스 이름을 가진다.
### 2.1.2 첫 REPL 앱 만들어보기
```js
<script>let name = 'Svelte';</script>
<h1>Hello {name}!</h1>
```

```js
<script>let name = 'Svelte';</script>
<h1>Hello {name}!</h1>
<label for="name">Name</label>
<input id="name2" value={name}>
```

```js
<script>let name = 'Svelte';</script>
<h1>Hello {name}!</h1>
<label for="name">Name</label>
<input id="name" on:input={event => name = event.target.value} value={name}>
```

```js
<script>let name = 'Svelte';</script>
<h1>Hello {name}!</h1>
<label for="name">Name</label>
<input id="name" bind:value={name}>
```

```js
<script>let name = 'Svelte';</script>
<h1>Hello {name}!</h1>
<label for="name">Name</label>
<input id="name" bind:value={name}>
<style>h1 {color: red;}</style>
```

Ex. 2-1 색 입력 기능까지 추가한 REPL 앱 코드
```js
<script>
	let color = 'red';
	let name = 'world';
</script>

<label for="name">Name</label>
<input id="name" bind:value={name}>

<label for="color">Color</label>
<input id="color" type="color" bind:value={color}>
<div style="background-color: {color}" class="swatch" />

<h1 style="color: {color}">Hello {name}!</h1>

<style>
	.swatch {
		display: inline-block;
		height: 20px;
		width: 20px;
	}
</style>
```

#### 리액티브 구문
`App.svelte`
```js
<script>
	let color = 'red';
	let name = 'world';
	let upper = false;
	$: greeting = `Hello ${name}!`;
	$: casedGreeting = upper ? greeting.toUpperCase() : greeting;
</script>

<label for="name">Name</label>
<input id="name" bind:value={name}>

<label for="color">Color</label>
<input id="color" type="color" bind:value={color}>
<div style="background-color: {color}" class="swatch" />

<label>
	<input type="checkbox" bind:checked={upper}>
	Uppercase
</label>
<h1 style="color: {color}">{casedGreeting}</h1>

<style>
	.swatch {
		display: inline-block;
		height: 20px;
		width: 20px;
	}
</style>
```

$:가 바로 리액티브 구문\_reactive statement\_이다. 리액티브 구문은 해당 구문이 참조하는 변숫값이 변경되면 다시 실행된다. 리액티브 구문에서 어떤 값을 변수에 할당하는 경우를 리액티브 선언문\_reactive declaration\_이라고 한다.

#### Props
`App.svelte`
```js
<script>
	import Clock from './Clock.svelte';
	
	let color = 'red';
	let name = 'world';
	let upper = false;
	$: greeting = `Hello ${name}!`;
	$: casedGreeting = upper ? greeting.toUpperCase() : greeting;
</script>

<label for="name">Name</label>
<input id="name" bind:value={name}>

<label for="color">Color</label>
<input id="color" type="color" bind:value={color}>
<div style="background-color: {color}" class="swatch" />

<label>
	<input type="checkbox" bind:checked={upper}>
	Uppercase
</label>
<h1 style="color: {color}">{casedGreeting}</h1>

<Clock />

<style>
	.swatch {
		display: inline-block;
		height: 20px;
		width: 20px;
	}
</style>
```

`Clock.svelte`
```js
<div>
	I will be a clock.
</div>
```

프롭스\_props\_를 통해 컴포넌트에 데이터를 전달할 수 있다.
스벨트는 export 키워드로 컴포넌트가 받아들일 수 있는 프롭스를 정의한다.

`App.svelte`
```js
<script>
	import Clock from './Clock.svelte';
	
	let color = 'red';
	let name = 'world';
	let upper = false;
	$: greeting = `Hello ${name}!`;
	$: casedGreeting = upper ? greeting.toUpperCase() : greeting;
</script>

<label for="name">Name</label>
<input id="name" bind:value={name}>

<label for="color">Color</label>
<input id="color" type="color" bind:value={color}>
<div style="background-color: {color}" class="swatch" />

<label>
	<input type="checkbox" bind:checked={upper}>
	Uppercase
</label>
<h1 style="color: {color}">{casedGreeting}</h1>

<Clock {color}/>

<style>
	.swatch {
		display: inline-block;
		height: 20px;
		width: 20px;
	}
</style>
```

`Clock.svelte`
```js
<script>
	export let color = 'blue';
	let hhmmss = '';
	setInterval(() => {
		hhmmss = new Date().toLocaleTimeString();
	}, 1000);
</script>

<span style="color: {color}">{hhmmss}</span>
```

### 2.1.3 REPL 앱 저장하기
REPL에서 만든 **앱을 저장**하려면 **‘Log in to save’** 버튼을 눌러 로그인 한 다음 디스크 아이콘을 누른다.
**저장한 앱**은 로그인 한 사용자의 프로필 아이콘에 팝업으로 나타나는 **‘Your saved apps’** 메뉴에서 확인할 수 있다.

포크\_fortk\_ 아이콘으로 현재 앱을 복제할 수 있다.

다운로드\_download\_ 아이콘을 누르면 svelte-app.zip 파일로 패키지를 다운로드한다.
다운 받은 패키지는 ‘npm Install’ 후 ‘rpm run dev’ 명령으로 확인할 수 있다.
```bash
~/svelte-app/ $ npm install

added 104 packages, and audited 105 packages in 12s

8 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
~/svelte-app/ $ npm run dev

> svelte-app@1.0.0 dev
> rollup -c -w

rollup v2.78.0
bundles src/main.js → public/build/bundle.js...
LiveReload enabled
created public/build/bundle.js in 153ms

[2022-08-18 13:02:45] waiting for changes...

> svelte-app@1.0.0 start
> sirv public --no-clear "--dev"


  Your application is ready~! 🚀

  - Local:      http://localhost:8080
  - Network:    Add `--host` to expose

────────────────── LOGS ──────────────────

  [13:02:58] 200 ─ 5.44ms ─ /
  [13:02:58] 200 ─ 0.61ms ─ /global.css
  [13:02:58] 200 ─ 1.04ms ─ /build/bundle.css
  [13:02:58] 200 ─ 1.49ms ─ /build/bundle.js
  [13:02:58] 200 ─ 0.39ms ─ /favicon.png

```

## 2.2 REPL 없이 개발하기
#### Install Home-brew
[https://brew.sh][8]

#### Install Node.js
[https://nodejs.org/][9]

#### Create Svelte App Directory
```bash
~/learn.svelte/ $ mkdir svelte-app
~/learn.svelte/ $ cd svelte-app 
```

#### Clone Svelte.js Template
```bash
~/svelte-app/ $ npx degit sveltejs/template           
Need to install the following packages:
  degit
Ok to proceed? (y) 
> cloned sveltejs/template#HEAD
~/svelte-app/ $ 
```
npx degit 커맨드로 스벨트 애플리케이션을 생성한다.

degit는 Rich Harris가 스벨트 프로젝트의 기본 골격을 쉽게 만들기 위해 NPX 커맨드로 개발했다.
‘de’ 접두어가 ‘\~에서 꺼낸다’라는 뜻으로 de-git는 git 저장소에서 미리 정의되어 있는 디렉토리 구조와 시작 파일들을 다운로드한다. 옵션을 지정하지 않으면 마스터 브랜치\_master branch\_의 내용을 가져온다.

npx degit sveltejs/template에서 sveltejs는 조직 이름이고 template는 저장소 이름이다.
- sveltejs/template는 [롤업][10] 모듈 번들러를 사용한다.
- sveltejs/template-webpack는 [웹팩][11] 모듈 번들러를 사용한다.
- 롤업, 웹팩 외에 [파셀][12]을 모듈 번들로러 사용하려면 플러그인으로 추가한다.  
	[https://github.com/DeMoorJasper/parcel-plugin-svelte][13]

자바스크립트 모듈 번들러는 다른 애플리케이션 관련 내용들과 애플리케이션이 필요로 하는 모든 자바스크립트 코드를 묶어서 하나의 자바스크립트 파일로 만든다. 이 과정을 통해 디펜던시가 있는 다른 자바스크립트 라이브러리 등을 다운로드하고 번들하기도 한다. 또한 사용하지 않는 코드 등을 제거해서 결과 파일을 최대한 작게 만든다. 이런 과정을 거침으로써 웹 브라우저가 자바스크립트 기반 앱을 다운로드하는 데 소요되는 시간을 최소화한다.
모듈 번들로러 가장 유명한 것이 롤업, 웹팩, 파셀이다. 롤업은 Rich Harris가 만들었다.

#### NPM Install
```bash
~/svelte-app/ $ npm install

added 97 packages, and audited 98 packages in 13s

6 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
~/svelte-app/ $ 
```

#### NPM Run
```bash
~/svelte-app/ $ npm run dev

> svelte-app@1.0.0 dev
> rollup -c -w

rollup v2.62.0
bundles src/main.js → public/build/bundle.js...
LiveReload enabled
created public/build/bundle.js in 106ms

[2021-12-26 13:35:45] waiting for changes...

> svelte-app@1.0.0 start
> sirv public --no-clear "--dev"


  Your application is ready~! 🚀

  - Local:      http://localhost:5000
  - Network:    Add `--host` to expose

────────────────── LOGS ──────────────────

```

npm run dev나 npm run build를 실행하면 public 디렉토리에 번들 파일들이 생성된다.
- bundle.css
- bundle.css.map
- bundle.js
- bundle.js.map

.map 파일은 애플리케이션 디버깅을 위한 파일이다. 여기에는 생성된 코드와 작성된 소스 코드 위치를 연결하는 정보가 담겨 있어서 디버거를 통해 코드를 살펴보거나 단계별로 코드를 실행하도록 해준다.

#### Test
```bash
Last login: Thu Aug 18 13:18:43 on ttys001
$ curl localhost:5000
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset='utf-8'>
	<meta name='viewport' content='width=device-width,initial-scale=1'>

	<title>Svelte app</title>

	<link rel='icon' type='image/png' href='/favicon.png'>
	<link rel='stylesheet' href='/global.css'>
	<link rel='stylesheet' href='/build/bundle.css'>

	<script defer src='/build/bundle.js'></script>
</head>

<body>
</body>
</html>
$ 
```

### 2.2.2 package.json
`package.json`
```json
{
  "name": "svelte-app",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "build": "rollup -c",
    "dev": "rollup -c -w",
    "start": "sirv public --no-clear"
  },
  "devDependencies": {
    "@rollup/plugin-commonjs": "^17.0.0",
    "@rollup/plugin-node-resolve": "^11.0.0",
    "rollup": "^2.3.4",
    "rollup-plugin-css-only": "^3.1.0",
    "rollup-plugin-livereload": "^2.0.0",
    "rollup-plugin-svelte": "^7.0.0",
    "rollup-plugin-terser": "^7.0.0",
    "svelte": "^3.0.0"
  },
  "dependencies": {
    "sirv-cli": "^1.0.0"
  }
}

```

package.json 파일을 통해 실행 환경을 확인할 수 있다.

devDependencies 필드를 통해 모듈 번들러로 롤업을 사용하는 것을 알 수 있다. 필요한 경우 롤업 대신 웹팩이나 파셀을 쓸 수 있다.

Dependencies 필드를 통해 스벨트 앱이 런타임에 sirv-cli만 필요로 한다는 것을 알 수 있다.
sirv-cli는 npm start 명령으로 실행되는 로컬 HTTP 서버이다.

### 2.2.3 중요 파일들
스벨트 앱에서 가장 중요한 시작 파일들은 **public/index.html, src/main.js, src/App.svelte** 이다. 물론 이 파일들은 필요한 경우 수정할 수 있다.

`public/index.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset='utf-8'>
	<meta name='viewport' content='width=device-width,initial-scale=1'>

	<title>Svelte app</title>

	<link rel='icon' type='image/png' href='/favicon.png'>
	<link rel='stylesheet' href='/global.css'>
	<link rel='stylesheet' href='/build/bundle.css'>

	<script defer src='/build/bundle.js'></script>
</head>

<body>
</body>
</html>
```

index.html에는 CSS 파일 두 개와 JavaScript 파일 하나를 불러온다.
- **global.css**에는 모든 컴포넌트에 영향을 주는 CSS가 선언되어 있다.
- **bundle.css**에는 .svelte 파일에 정의된 각 컴포넌트에 영향을 주는 CSS가 선언되어 있다.
- **bundle.js**에는 .svelte 파일의 정의된 각 컴포넌트에서 사용하는 JavaScript 코드가 선언되어 있다.

`src/main.js`
```js
import App from './App.svelte';

const app = new App({
	target: document.body,
	props: {
		name: 'world'
	}
});

export default app;
```

main.js는 Svelte App 컴포넌트를 화면에 그린다.
- **target** 속성은 컴포넌트가 어디에 그려져야 하는지 지정한다.
-  **props**로 컴포넌트에 데이터를 전달한다.  
	데이터 전달은 App.svelte에서 정의할 수 있어서 main.js에서 props를 사용할 필요는 없다.

> export default app;
main.js는 최상위 컴포넌트의 인스턴스를 만들고 default로 export 한다.

`src/App.svelte`
```js
<script>
	export let name;
</script>

<main>
	<p>Hello, world!</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
```

.svelte 파일은 script, main, style 요소를 가진다. 이 세 가지는 필수는 아니며 필요한 것만 기술하면 된다.

각 요소의 순서는 중요하지 않지만 일반적으로 script, main, style 순서로 사용한다. 이는 각 요소가 어떤 순서로 영향을 받는지를 보여준다. 일반적으로 script는 HTML(main)에서 사용되고, HTML의 스타일은 CSS(style)에 의해 결정되기 때문이다.

```js
<script lang='ts'>
```
script를 TypeScript를 사용하려면 lang 속성을 ‘ts’로 지정하면 된다.

```js
<script lang='ts'>
	export let name;
</script>
```
export 키워드는 let name 변수가 props라는 것을 선언한다.

### 2.2.4 로컬에서 개발하는 첫 앱

# Part 2. 스벨트 파헤치기
# Chapter 3. 컴포넌트 만들기

.svelte 파일은 상태와 로직을 정의하는 JavaScript 코드, 화면을 그리기 위한 HTML, 그리고 이를 꾸미는 CSS로 이루어져 있다.

컴포넌트는 밀접한 연관성을 가지는 UI 요소들의 집합이다. 컴포넌트는 특정 UI와 밀접한 데이터, 즉 ‘상태’를 관리한다. 이런 특성 때문에 컴포넌트는 재사용이 가능한 UI 구성 요소가 될 수 있다.

컴포넌트는 자신을 사용하는 컴포넌트로부터 Props로 데이터를 전달받을 수 있다.

컴포넌트의 상태는 각 컴포넌트 인스턴스별로 고유하다.
컴포넌트의 로직은 이벤트 핸들링 등 컴포넌트가 어떻게 동작할지를 정의하는 함수 집합으로 구성된다.

CSS 규칙은 전역으로 선언해서 모든 컴포넌트에 영향을 미칠 수 있다. 하지만 스타일 요소가 유효 범위를 가지도록 만들어지면, 스타일이 정의된 곳의 컴포넌트에만 영향을 미친다.

리액티브 구문은 변수 값이 바뀔 때 코드를 다시 실행한다. 이런 리액티브 구문은 일반적으로 상태변수를 다시 계산해서 바꾸며, 그에 따라 UI의 일부가 다시 그려진다.

모듈 컨텍스트를 쓰면 컴포넌트의 모든 인스턴스가 특정 내용을 공유하게 만들 수 있다.

## 3.1 .svelte 파일에 담기는 것
```js
<script>
	// JavaScript Codes
</script>

<!-- HTML Elements -->

<style>
	/* CSS Rules */
</style>
```

\<script\>와 \<style\> 내에 작성되는 JavaScript 코드와 CSS 규칙은 해당 컴포넌트에 대해서만 유효하다. 다시 말해 다른 컴포넌트들은 코드를 볼 수 없다는 뜻이다. 그래서 코드나 스타일이 실수로 다른 컴포넌트에 영향을 미치는 일이 없고 디버깅도 쉬워진다.

## 3.2 컴포넌트 마크업
스벨트 컴포넌트의 인스턴스는 Props를 Childs를 전달받을 수 있다.
Props로 컴포넌트에 데이터를 전달하고, Childs로 컴포넌트에 컨텐츠를 전달한다.
Childs는 Text, HTML, 그 외 다른 스벨트 컴포넌트들로 구성될 수 있다.

HTML Attribute는 HTML Element에 명시되는 반면, Props는 DOM에 해당하는 JavaScript Object의 Property가 된다.

Props의 값은 Boolean, Numeric, String, Object, Array, Function 등 어떤 타입이 될 수도 있고 JavaScript 표현식의 값이 될 수도 있다.

HTML Element로 전달되는 Props의 값이 null 또는 undefined 인 경우, 이 속성은 DOM에 추가되지 않는다.

```js
<Person fullName="{lastName}, {firstName} {middleName[0]}." />
```
문자열 값은 JavaScript 표현식에 따라 값을 계산하기 위해 보간`interpolate` 될 수 있다.
문자열 내부에 있는 중괄호 표현식은 표현식 값으로 대체된다.

```js
<Person {fullName} />
```
Props 값을 전달하기 위해 쓰는 변수의 이름이 Props의 이름과 같은 경우 코드를 더 짧게 쓸 수 있다.

```js
<script>
	let score = 0;
	const scoreAttrs = {
		type: 'number',
		max: 10,
		min: 0
	};
</script>
<input {...scoreAttrs} bind:value={score}>
```
JavaScript 전개\_spread\_ 연산자는 값이 Props 값인 객체를 Props 처럼 전달할 때 쓸 수 있다.

```js
<html>
	<head>
		<script>
			function log() {
				const input = document.querySelector('input');
				console.log('DOM prop value = ', input.value);
				console.log('HTML attr value = ', input.getAttribute('value'));
			}
		</script>
	</head>
	<body>
		<label>
			Name <input value="initial" />
		</label>
		<button onClick="log()">Log</button>
	</body>
</html>
```
몇몇 DOM Property는 HTML Attribute에서 초기값을 가져온다. 이런 DOM Prperties는 그 값이 바뀌기도 하지만 관련된 HTML Attribute 값은 절대로 변하지 않는다. 위 코드에서 “initial”로 정의된 input 태그의 속성값을 변경하면 DOM Property 값은 변경되지만 HTML Attribute의 값은 변하지 않는다.

또한 몇몇 HTML Attribute는 DOM Property로 연결되지 않기도 한다. 이를테면 table 태그 안에 쓰이는 td 태그의 colspan이 이에 해당한다.

몇몇 DOM 속성은 연관된 HTML 속성이 없기도 하다. 예를 들어 DOM의 textContent Property와 연관된 HTML Attribute는 없다.

이런 기술적인 내용과 무관하게 **Svelte 컴포넌트는 HTML Attribute를 가지지 않는다. 대신 Props만 가진다.**

## 3.3 컴포넌트 이름
```js
<script>
	import Other from './Other.svelte';
</script>

<main>
	<Other/>
</main>
```
Svelte 컴포넌트를 정의할 때는 컴포넌트 이름을 명시하지 않는다. 대신 .svelte 파일을 불러오는 경우에만 컴포넌트 이름을 명시한다. 다시 말해 불러올 때 지정한 이름이 컴포넌트 이름이 된다.

컴포넌트 이름은 반드시 대문자로 시작해야 한다.

일반적으로 소스 파일 이름과 컴포넌트 이름을 같게 하는 경우가 많지만, 반드시 그래야 할 필요는 없다.

## 3.4 컴포넌트 스타일
```js
<script>
	let status = 200;
	let message = "This is a message.";
</script>

<main>
	<label>
		Status <input type="number" bind:value={ status }>
	</label>

	<div class:error={ status >= 400 }>{ message }</div>
	<div class={ status >= 400 ? 'error' : '' }>{ message }</div>
</main>

<style>
	.error {
		color: red;
		font-weight: bold;
	}
</style>
```
CSS 규칙은 HTML element에 여러 방법으로 조건부 적용할 수 있다.

또 다른 방법은 같은 이름을 가지는 불리언 변수를 사용한 리액티브 선언문을 script에 추가하는 것이다.
```js
<script>
	let status = 200;
	let message = "This is a message.";

	$: error = status >= 200;
</script>

<main>
	<label>
		Status <input type="number" bind:value={ status }>
	</label>

	<div class:error>{ message }</div>
</main>

<style>
	.error {
		color: red;
		font-weight: bold;
	}
</style>
```
$: 문법은 리액티브 구문이라고 한다.
이 구문이 참조하는 어떤 변수값이 바뀌면 해당 구문이 다시 실행된다.
위 코드의 경우 status 변수값이 바뀌면 error 값 역시 다시 계산된다.

Svelte는 CSS를 생성할 때 사용하지 않는 CSS 규칙은 자동으로 제거한다. 제거 대상이 되는 CSS 규칙은 컴포넌트에 의해 화면에 표시될 수 있는 HTML element와 일치하는 것이 하나도 없는 것이다.
Svelte 컴파일러는 사용하지 않는 CSS 규칙에 대해서 경고 메시지를 출력한다.

## 3.5 CSS 명시도
CSS 명시도\_specificity\_는 CSS 규칙이 충돌할 때 어떤 규칙을 지정할지 결정하는 방법이다.

CSS 규칙에 대한 명시도는 네 개의 숫자로 표현된다.
- 첫 번째 숫자는 **인라인 스타일**인 경우 1, 아니면 0이다.
- 두 번째 숫자는 지정자 안의 **id 값**이다.
- 세 번째 숫자는 지정자 안의 **클래스 이름 갯수**이다.
- 네 번째 숫자는 지정자 안의 **요소 이름에 대한 참조 수**이다.

HTML 요소 내의 style 속성으로 지정된 CSS 규칙이 항상 가장 높은 순위를 가진다. 그다음 id 속성이 클래스 이름보다 더 중요하고, 클래스 이름은 요소 이름보다 앞선다.

```js
<script>
	
</script>

<main>
	<div class="parent">
		I am the parent.
		<div id="me" class="child" style="color:red">
			I am the child.
		</div>
	</div>
</main>

<style>
	#me {
		color: orange;
	}
	.parent > .child {
		color: yellow;
	}
	.parent .child {
		color: green;
	}
	.child {
		color: blue;
	}
	.parent {
		color: purple;
	}
</style>
```
- .parent \> #me는 0.1.0.0이다.
- .parent #me의 점수도 0.1.0.0이다.
- .parent .child 점수는 0.2.0.0이며 is를 지정한 것보다 더 낮은 점수를 가진다.

## 3.6 유효 범위를 가지는 스타일과 전역 스타일
젼역 스타일은 애플리케이션의 모든 컴포넌트에 똑같이 적용되어야 하는 스타일에 적합하다.

유효 범위를 가지는 스타일은 다른 컴포넌트에 영향을 주지 않고 해당 컴포넌트에만 스타일을 지정할 때 쓴다.

스벨트 컴포넌트 내의 style 요소에 정의한 CSS 규칙은 해당 컴포넌트에 대해서만 유효 범위를 가지며 다른 컴포넌트에는 영향을 주지 않는다. 스타일의 유효 범위는 svelte-hash 형태로 CSS 클래스 이름을 생성하고 적용하는 방식으로 지정된다.

전역 스타일을 지정하는 두 가지 방법이 있다.
`public/global.css`
```js
h1 {
	color: red;
}
```
첫 번째는 public/global.css 파일에 스타일을 정의하는 것이다. 이 파일은 public/index.html 파일이 기본으로 불러오는 스타일이다.

```js
<style>
	:global(h1) {
		color: red;
	}
</style>
```
두 번째 방법은 컴포넌트의 style 요소 안에 :global 셀렉터로 스타일을 정의하는 것이다.

전역 스타일의 CSS 속성은 컴포넌트의 style 요소가 정의하지 않은 속성에 한해 컴포넌트에 적용된다.

h1 지정자를 정의하면 스벨트 컴파일러는 h1.svelte-hash 클래스 이름을 가지는 규칙으로 컴파일한다. :global(h1) 지정자를 쓰면 유효 범위가 
```js
<h1>Pony for sale</h1>
<p class="description">2 year old Shetland pony</p>

<style>
	:global(h1) {
		color: red;
	}
	h1 {
		color: red;
	}
	.description {
		font-style: italic;
	}
</style>
```

`pbulic/build/build.css`
```js
h1{color:red}
h1.svelte-xp2tfb{color:green}
.description.svelte-xp2tfb{font-style:italic}
```
스벨트 컴파일러는 h1.svelte-hash 클래스 이름을 가지는 규칙으로 컴파일한다. :global(h1) 지정자를 쓰면 유효 범위가 없는 규칙을 만든다.

:global 수식자를 쓴 CSS 규칙의 속성은 public/global.css에 정의된 동일한 CSS 지정자의 속성값을 덮어쓴다.
:global 수식자는 또한 하위 컴포넌트의 스타일을 덮어쓰기 위한 목적으로도 사용된다. 하위 컴포넌트 스타일을 덮어쓰려면 더 높은 명시도를 가지는 CSS 규칙을 만들어야 한다.
:global 수식자는 반드시 CSS 지정자 목록의 처음이나 끝에만 써야 한다. 중간에 쓰는 것은 허용되지 않는다.

```js
<style>
	.user :global(.address .city) { ... }
</style>
```
:global 수식자에는 CSS 지정자 목록을 넘길 수도 있다.

## 3.7 CSS 전처리기
스벨트 모듈 번들러는 CSS 전처리기를 쓸 수 있다. CSS 전처리기는 표준 CSS에서는 지원하지 않는 사용자 정의 스타일 문법을 읽어 와서 표준 CSS로 바꾸는 일을 한다.

```js
<style lang="scss">
```
예를 들어 [Sass][14]를 CSS 전처리기로 사용하려면 style 요소에 lang 속성을 지정하면 된다.

## 3.8 컴포넌트 로직
컴포넌트 로직은 두 가지 방법으로 정의할 수 있다. 첫 번째는 **script 요소 내에 자바스크립트 함수**를 정의하는 것이다. 두 번째는 **HTML 요소 내에 블록 구조**를 쓰는 것이다.

## 3.9 컴포넌트 상태
script 요소 내의 지역 변수가 아닌 변수가 HTML 보간에서 참조하는 변수들은 해당 컴포넌트의 상태\_state\_로 간주된다. 여기서 보간은 중괄호 안에 있는 JavaScript 표현식을 의미한다. 이런 상태 변수들의 값을 변경하게 되면 해당 변수를 사용하는 보간들의 표현식이 다시 계산된다. 그리고 새로 계산된 값이 이전과 다르면 해당 DOM 부분은 업데이트 된다.

## 3.10 리액티브 구문
최상위 수준의 구문, 즉 함수 내부나 코드 블록 안에 있지 않는 구문에 달러 기호($)의 레이블로 시작하는 구문을 Svelte는 리액티브 구문으로 간주한다.

JavaScript는 동일한 유효 범위 내에서 동일한 레이블 이름을 여러 번 쓰는 것을 에러로 처리하지 않는다. 그래서 리액티브 구문도 여러 번 쓸 수 있다.

리액티브 구문은 해당 구문이 참조하는 변수 중 어떤 것이라도 그 값이 바뀌면 다시 실행된다.

```js
<script>
	$: average = total / count;
	$: console.log('count = ', count);
</script>
```
위에서 첫 번째 구문은 리액티브 선언문이고 두 번째는 리액티브 구문이다.

선언되지 않은 변수 앞에 $: 레이블을 붙이는 경우 Svelte는 리액티브 구문 변수 앞에 let 키워드를 삽입한다.

```js
<script>
	$: isTeen = 13 <= age && age < 20;
	$: upperName = name.toUpperCase();
</script>
```
위와 같은 리액티브 선언문들은 아래와 같은 반응성 블록으로 대체할 수도 있다.
```js
<script>
	let isTeen, upperName;
	$: {
		isTeen = 13 <= age && age < 20;
		upperName = name.toUpperCase();
	}
</script>
```

```js
<script>
	$: if (someCondition) {
		// ...
	}
</script>
```
$: 구문의 if 구문은 조건문이나 if 구문의 바디에서 참조하는 변수값이 바뀌면 다시 실행된다. 만약 조건문이 함수 호출을 포함하고 있다면 if 구문의 변수값이 바뀔 때마다 해당 함수도 다시 호출된다.

```js
<script>
	let diameter = 1;
	let height = 1;

	$: volume = area * height;
	$: area = Math.PI * radius ** 2;
	$: radius = diameter / 2;
</script>

<main>
	<h1>Cylinder Calculations</h1>
	<label>
		Diameter <input type="number" bind:value={ diameter }>
	</label>
	<label>
		Height <input type="number" bind:value={ height }>
	</label>
	<label>Radius: { radius }</label>
	<label>Area: { area.toFixed(2) }</label>
	<label>Volume: { volume.toFixed(2) }</label>
</main>

<style>
	input {
		width: 50px;
	}
</style>
```
리액티브 선언문은 위상 순서에 따라 실행된다. 위 코드에서는 diameter, radius, area, volume 순서로  변경이 일어난다.

리액티브 선언문은 실제 실행되는 순서와 동일하게 배치하는 것이 읽기도 편하고 이해하기도 쉽다. 위 코드의 리액티브 구문은 radius, area, volume 순서로 코드를 배치하면 이해하기 쉬워진다.

Svelte는 리액티브 선언문들 사이에 순환 참조가 발생하는 것을 탐지할 수 있으며 이에 대한 에러를 표시한다.(‘Cyclical dependency detected.’)

## 3.11 모듈 컨텍스트
Svelte는 Module Context를 통해 자신을 포함하는 코드를 가리킬 수 있는 사용자 정의 script 요소 속성을 정의할 수 있다.
```js
<script context="module">
	...
</script>
```
script 요소에 context를 명시하면 모듈 컨텍스트_module context_가 된다.
script 요소에 context를 별도로 명시하지 않으면 이는 인스턴스 컨텍스트_instance context_이다.

모듈 컨텍스트에서는 해당 컴포넌트의 모든 인스턴스에서 접근할 수 있는 변수와 함수를 정의할 수 있다. 모든 인스턴스에서 데이터를 공유할 수 있는 것이다. 하지만 모듈 컨텍스트에서 정의하는 변수들은 반응성이 없기 때문에 이들 변수가 바뀐다고 해서 컴포넌트가 업데이트되지는 않는다. 그리고 모듈 컨텍스트에서는 인스턴스 컨텍스트에 정의된 변수나 함수에 접근할 수 없다.
JavaScript 코드를 인스턴스가 생성될 때마다 실행하는 것이 아니라 딱 한 번만 실행하고 싶다면 코드를 모듈 컨텍스트로 정의하면 된다.

Svelte는 컴포넌트가 정의한 로컬 상태에 의존하지 않는 모든 함수는 그 선언부를 상단으로 끌어올린다.

모듈 컨텍스트에 함수를 정의하면 소스 파일 바깥에서 이 함수를 불러와서 사용할 수 있다. 물론 .svelte 파일은 기본 내보내기_export_ 대상을 명시할 수 없다. Svelte는 컴포넌트를 정의하고 컴포넌트가 항상 기본 내보내기 대상이 되기 때문이다.

`/src/Demo.svelte`
```js
<script context="module">
	export function add(n1, n2) {
		return n1 + n2;
	}
</script>

<main>
	Demo Module.
</main>
```

`/src/App.svelte`
```js
<script>
	import { onMount } from 'svelte';
	import { add } from './Demo.svelte';

	onMount(() => {
		const sum = add(1, 3);
		console.log("sum = ", sum);
	});
</script>

<main>
	Hello, world!
</main>
```

위와 같이 구성하는 것도 가능하지만 이런 유틸리티 함수들을 정의하는 것은 .svelte 파일 보다는 .js 파일을 사용하는 것이 일반적이다.

# Chapter 4. 블록 구조

[2]:	https://www.youtube.com/watch?v=gJ2P6hGwcgo
[3]:	https://github.com/sveltejs/sapper
[4]:	https://nativescript.org
[5]:	https://svelte-native.technology
[6]:	https://node.js.org
[7]:	https://svelte.dev/repl
[8]:	https://brew.sh/index_ko
[9]:	https://nodejs.org/
[10]:	https://rollupjs.org
[11]:	https://rollupjs.org
[12]:	https://parceljs.org
[13]:	https://github.com/DeMoorJasper/parcel-plugin-svelte
[14]:	https://sass-lang.com