## 반응형 웹 디자인

부모요소에 의해서 사이즈가 변경이 되어야 한다면, %나 em을 쓰면 되고, 부모와는 상관없이browser 사이즈에 따라서 사이즈가 변경이 되어야 한다면, vh, vw, rem을 쓰면된다.

요소의 너비와 높이에 따라서 사이즈가 변경이 되어야 한다면 %나 vh,vw같은 것을 사용하면 되고, 폰트 사이즈에 따라서 사이즈가 변경이 되어야 한다면 em과 rem을 사용하면 된다.

폰트 사이즈는 rem으로 쓰는게 좋고, padding이나 margin같은 경우는 그 요소의 크기에 따라서 변경될 수 있게, em으로 쓰는게 좋다!


### 가변 그리드 공식 이해하기

(가변 크기로 만들 박스의 가로 너비 % 가변 크기로 만들 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 크기의 값
(960px % 300px) * 100 = 31.25
```
    <div class="big"> //width 90%
        <div class="small"></div> // width: 31.25%
    </div>
```
이 두개의 박스는 저 가로 비율에 맞춰 움직인다.

### 가변 마진과 가변 패딩 이해하기

* 가변 마진 적용
(가변 마진을 적용할 마진값 % 적용할 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 마진값
```
<div id="wrap">
   <div class="red"></div>
   <div class="blue"></div>
</div>
```
.wrap{
  width: 90%;
  margin: 0 auto;
  border: 2px solid #000;
}
div{
  display: inline-block;
  width: 31.25%;
  height: 300px;
}
.red{
  margin-right: 37.5%;
  background: red;
}
.blue{
  background: blue;
}
화면으로 띄워서 확인.

* 가변 패딩 적용 방법 1,2번 예제
(가변 패딩을 적용할 패딩값 % 적용할 박스를 감싸고 있는 박스의 가로 너비) * 100 = 가변 패딩값
```
<div id="wrap">
	<p> 이름 </p>
</div> 
```
//css
// 960px 에서 padding이 40이라고 할때..!
#wrap{
	width: 90%;
	margin: 0 auto;
	background: yellow;
	height: 500px;
}
p{
	padding: 40px 4.16%;
}

```
<div id="wrap">
	<p> 이름 </p>
</div> 
```
//css
//p태그의 가로너비는 600px을 넘지 않으면서 양쪽에는 40px의 패딩값 적용. 가로값이 변경될때 비율에 맞춰서 적용된다.

#wrap{
	width: 90%;
	margin: 0 auto;
	border: 4px solid black;
}
p{
	width: 54.66%;
	padding: 40px 4.16%;
	margin: 0 auto;
	background: yellow;
}

### px을 %로 바꾸기

가변 폰트 이용하기 rem, em

(가변 폰트를 적용할 글자 크깃값 % 적용할 요소를 감싸고 있는 요소의 글자 크깃값) = 가변 폰트값

rem. 웹 문서의 시작인 html 태그를 기준으로 하기 때문에 상속 문제가 발생하지 않아 유용하게 사용할 수 있는 단위 중 하나.

```
<div class="para">
가변 폰트	
	<p>가변 폰트2</p>
</div>
```
//css 1번 예제
*{font-size: 16px;}
.para{
	font-size: 4em;
		p{
			font-size: 2em;
		}
	}
//para는 64px, p는 128px이 된다.
//p의 font-size를 0.5em으로 하면 p는 32px이 된다. 50% 이렇게 지정해 줄수도 있다.

//css 2번 예제
*{font-size: 16px;}
.para{
	font-size: 4em;
		p{
			font-size: 2rem;
		}
	}
//para는 64px, p는 32px이 된다. 

- vw, vh, vmin, vmax 단위를 사용하면 브라우저의 비율에 따라 글자 크기가 늘어나거나 줄어든다.
    - vw: 브라우저의 width 기준
    - vh: 브라우저의 height 기준
    - vmin: width, height 중에 더 작은 사이즈 기준
    - vmax: width, height 중에 더 큰 사이즈 기준
(vw, vh, vmin, vmax 단위를 적용할 글자 크깃값 * 브라우저의 너빗값) / 100 = 크깃값

### 가변적인 멀티미디어 요소 만들기

width: 100%,
max-width: 100%
두개의 속성 모두 주기

### 미디어쿼리 이해하기. 
미디어 쿼리의 기본문법
[only 또는 not] @media [미디어 유형] [and 또는, 콤마] (조건문) {실행문}
(and 또는 콤마를 사용할때는 그 뒤에 공백 한글자를 넣어야 미디어쿼리가 정상적으로 작동한다.)
[미디어 유형]은 거의 screen
조건문 접두사인 min/max를 사용할 때 min 접두사는 반드시 크기가 작은 순서대로 작성해야 하고, max 접두사를 사용할 때는 반드시 크기가 큰 순서대로 작성해야된다. 순서를 반드시 지켜야 함.
미디어쿼리를 사용해서 브라우저의 크기를 감지할때는 html 문서 크기를 기준으로 감지한다.