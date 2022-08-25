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
