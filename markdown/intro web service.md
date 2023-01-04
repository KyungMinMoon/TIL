# What? Why? How?

##
웹서비스

웹 : 인터넷에 연결된/
컴퓨터들을 통해/
사람들이 정보를 주고 받을 수 있는 정보 공간

서비스 : 요청하고 응답(yes or no)하는 것

요청의 종류

1. 줘라/받아라 (get) : 달라고 했을 때, 주면 그게 get!
2. 보내라(post)

대체적으로 요청은 user가 하고, 응답은 program이 한다.

=> 서버컴퓨터에서 요청과 응답을 처리할 프로그램을 개발한다.

---

### static web(정적인)

서점 책처럼 본인이 알아서 나오는 게 아니라 그 자리에 그대로 있다.

### dynamic web(<-> static)

URL(uniform resource locator) : 컴퓨터 네트워크 상에서 자원이 어디 있는지 알려주기 위한 규약

### hyper text transfer protocol(http)

Markup : 역할표시(훨씬 보기 편하고, 가독성이 좋아지는 거)

ex)형광펜으로 밑줄긋기

### html

<!DOCTYPE html>

<html>
  <head>
    <meta charset="utf-8">
    <title>Hello HTML5</title>
  </head>
  <body>
    <!-- 주석(comment) -->
    <h1>Hello World</h1>
    안녕하세요 반갑습니다
    <p>안녕하세요</p>
  </body>  
</html>

```
<!DOCTYPE html> 
: 새해인사처럼 앞에 있어야 하는거! 

<body>: 실제 데이터
<head> : 메타 데이터

-> body는 브라우저에 표시되지만, head는 표시되지 않는다.
그래서 <body>가 더 중요! (head보다는)

"utf-8" - 유니코드를 위한 가변 길이 문자 인코딩 방식

<title> 태그는 웹 탭의 제목으로 나와

<h1>(body 태그 안에 중첩되어있는 h1)
 태그는 headline1으로 헬로우 월드로 표시를 하는거야. **중요표시**
h1이 두개일 수 없어! 크게 하려고 h1 쓰면 안 됨!

<p1>(body 태그 안에 중첩되어있는 p1)

<!-- paragraph => Block -->
<p>문단을 나누고 싶으면 p로 감싼다</p>

    안녕하세요
    반갑습니다
```

```
alt + 방향키 : 원하는 곳으로 이동
alt + b : 크롬에서 미리보기
ctrl + enter : 다음줄로 넘어가기
h1에 바로 tab: 태그 안에 자동으로 괄호
```
## 시맨틱 웹

```html
<body>
    <p>This is <strong>strong</strong> text</p>
    <p>This is <b>bold</b> text</p>
    <p>this is <em>em</em> text</p>
    <p>this is <i>italic</i> text</p>
```

```
저 위에서 <b> <i>는 중요도가 없고 의미하는 바도 없어서 알기 어려워. 
그래서 쓸 수도 없어!

=> <strong>과 <em>을 써야 한다.
```

```
작성자가 쓰고 볼 때 enter가 편하지만, 보는 사람은 이어지는 것처럼 보인다.

=> 문단을 나누고 싶으면 p로 감싼다.
=> 문장에서 단순 엔터를 하고 싶다면 <br>을 쓴다.
```

```html
<a> </a>는 아무 쓸데가 없어
a + tab누르면 

<a hef="google.com">Google</a>

    <!-- 새탭에서 열기 -->
<a hef="https://google.com"target="_blank">Google</a>

```
    ul>li*3

---
list
```html
    <h1>List</h1>
    <!-- ol,ul => Block -->
    <h2>Order List</h2>
    <p>순서 있는 리스트(ol)은 순차적인 리스트에 사용한다.</p>
    <ol>
        <li>손씻기</li>
        <li>양치하기</li>
        <li>숙면</li>
    </ol>

    <h2>Unordered List</h2>
    <p>순서 없는 리스트(ul)은 순서 없는 리스트에 사용한다.</p>
    <ul>
        <!-- ul>li*3 -->
        <li>사과</li>
        <li>바나나</li>
        <li>복숭아</li>
    </ul>
```

---
06_table
```html

    <h1>Table</h1>
    <!-- Table => Block -->
    <table>
        <thead>
            <tr>
                <th>이름</th>
                <th>나이</th>
                <th>성별</th>
            </tr>
            <td>문경민</td>
            <td>25</td>
            <td>여자</td>
        </thead>
    <tbody>
        <tr>
            <td>송원지</td>
            <td>26</td>
            <td>여자</td>

        </tr>
        <tr></tr>
        <tr></tr>

rowspan(열합치기)
colspan(행합치기)
```

---
07_image
```html
 <h1>Images</h1>

    <img width="700" height="500" src="./gunhoo.png" alt="">
    <img width="200" height="100" src="http://images.khan.co.kr/article/2019/09/07/l_2019090602000329100066416.jpg" alt="">
이미지는 선이다(inline)
alt = alternative로 
```

---
08_layout
```html
- 메뉴 전체 목록에서 '전체'만 칠하고 싶을 때 드래그 하는 용도로 span을 사용한다.

nav(navigation), header, section, article, footer, aside

<nav>네비게이션 바</nav>
<header>헤더</header>
<aside>사이드바</aside>
<section>하위 article들을 모으는 상위 구역</section>
<article>실제 기사나 게시글</article>
<footer>최하단 푸터</footer>
```

---
09_form
```python
    <form action="">
        <div>
            <input type="text" value="과거(기존) 데이터">
        </div>
        <div>
            <input type="email" placeholder="example@gmailcom">
        </div>
        <div>
            <input type="password">
        </div>
        <div>
            <input type="number">
        </div>
            <input type="checkbox", value="appble">사과
            <input type="checkbox", value="banana">바나나
            <input type="checkbox", value="strawberry">딸기

            # input 태그 밖에 있는 사과를 컴퓨터가 글자라고 인식하기 어렵다. 그래서 value를 써야한다! 1로 쓰면 서버에서는 1로 받아들인다.
```

web 1.0 -> 편성해 주는 것만 받아(TV)
web 2.0 -> 소통(라디오 사연 보내기, 인터넷에 글쓰기 가능)
web 2.99 -> creator
web 3 -> 지분 가지는 거 가능

---
form
```html
        <div>
            <label for="my-name">이름:</label>
            <input id="my-name"type="text" value="과거(기존) 데이터">
        </div>
        
        그냥 이름:<input id="my-name"type="text" value="과거(기존) 데이터"> 이렇게 써도 나오기는 하지만, 이름이라는 타이틀이 옆에 칸과 연결되어있는지를 모르기에, <label for="my-name">을 쓴다.


```
Q. 질문!
그 자동으로 다음 칸으로 넘어가는 방법은?
생년월일 입력할 때, 달력이 나오는 방법과, 달력 모양은 어떻게 설정하는지?