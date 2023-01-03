# CSS(Cascading Style Sheets)
html 없으면 존재의 이유가 없는 css이기에 html을 쓴다.


1. 셀렉터(Selector)
   h1{color:red;font-size:12px}
   h1 얘한테 빨간 색을 입히고 12포인트의 사이즈를 입힌다.


   ```html
    <style>
        p {
            font-size: 24px;
            color: blue;
        }
    </style>
    </head>
    <body>
    <!-- CSS 적용 3가지 방법 -->

    <!-- Inline CSS(밑에처럼 안 씀- 비효율적이라) -->
    <p style="font-size: 32px; color: red;">This is Big Red</p>    

    <!-- <head> Style Tag -->
    <p>This is Medium Blue</p>

    <!-- File .css -->
    <p>This is Small Green</p>
    </body>
    </html>

    이거를 미리보기 하면 medium blue랑 small green 모두 파란색으로 바뀌어. 그 이유는 위의 style에서 p전체를 하기 때문에 밑에 p 써있는 애들이 다 바뀌는거지!

   ```

   컴퓨터에 내장되어 있는 기본값이 있지만 리셋할 수 있음!

   ```html
    <!-- color 어트리뷰트는 자식 요소에 상속된다. -->
        <style>
        * {
            color: blue;
        }
        .container{
            color: red;
        }
    </style>
    </head>
    <body>
    <h1>Selector</h1>
    <div class="container">
        <p>Hello</p>
        <p>World</p>
    </div>
   ```

    ```html
        <div>
        <p>paragraph 1</p>
        <p>paragraph 2</p>
        <span><p>paragraph 3</p></span>

        위에서 1 2는 직계 자손, span 다음의 p 3은 손자 개념으로 생각!


        (자식 요소)와 (후손 요소)는 다르다!
        div 안에 있는 모든 p가 다 red(자식이고 후손이고 상관없이)
        
     <style>
        div > p { color: red; }
     </style>
     </head>
     <body>
     <h1>Heading</h1>
     <div>
     <p>paragraph 1</p>
     <p>paragraph 2</p>
     <span><p>paragraph 3</p></span>
    ```
