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