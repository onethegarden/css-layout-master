# (s)css-layout-master

> css layout master study
>
> <p style="font-size:8px">https://nomadcoders.co/css-layout-masterclass</p>

## 목차

- [1.1 First Rule of Flexbox](#11-First-Rule-of-Flexbox)
- [1.2 Main Axis and Cross Axis](#12-Main-Axis-and-Cross-Axis)
- [1.3 Column and Row](#13-Column-and-Row)
- [1.4 align-self and order](#14-align-self-and-order)
- [1.5 wrap, nowrap, reverse, align-content](#15-wrap-nowrap-reverse-align-content)
- [1.6 flex-grow, flex-shrink](#16-flex-grow-flex-shrink)
- [1.7 flex-basis](#17-flex-basis)
- [2.2 CSS Grid Basic Concepts](#22-css-grid-basic-concepts)
- [2.3 Grid Template Areas](#23-Grid-Template-Areas)
- [2.4 Rows and Columns](24-Rows-and-Columns)
- [2.5 Shortcuts](#25-Shortcuts)
- [2.6 Line Naming](#26-Line-Naming)
- [2.7 Grid Template](#27-grid-template)
- [2.8 Place Items](#28-Place-Items)
- [2.9 Place Content](#29-Place-Content)
- [2.10 Auto Columns and Rows](#210-Auto-Columns-and-Rows)
- [2.11 minmax](#211-minmax)
- [2.12 auto-fit auto-fill](#212-auto-fit-auto-fill)
- [2.13 min-content max-content](#213-min-content-max-content)

---

#### scss

- [3.0 CSS Preprocessors and Set Up](#30-CSS-Preprocessors-and-Set-Up)

- [3.1 Variables and Nesting](#31-Variables-and-Nesting)

<br/><br/><br/>
<br/><br/><br/>
<br/><br/><br/>

## 1.1 First Rule of Flexbox

- box를 정렬시킬 때 부모의 값이 (parent) 자식의 값(children)을 정렬시킬 수 있음

<br/><br/><br/><br/><br/>

## 1.2 Main Axis and Cross Axis

![image](https://user-images.githubusercontent.com/51187540/113576577-c5854280-965a-11eb-93aa-65ea7ba8245d.png)

- flexbox css 두 종류가 있음

1. row (Main Axis) : 행, 가로

2. column (Cross Axis) : 열, 세로

<br/><br/><br/>

- **justify-content** : <u>가로로</u> children 을 정렬함

  - center : 가운데 정렬

  - space-between : box사이의 공간

  - space-around : box사이에 공간이 일정하게 생김

<br/><br/><br/>

- **align-item** : <u>세로로</u> children들을 정렬함( 단, wrapper 에 대한 정렬임)

  - center : 가운데 정렬

  - stretch : wrapper에 맞게 늘림(단 children의 height이 없어야 함)

  - flex-start : 처음에 맞춤

<br/><br/><br/><br/><br/>

## 1.3 Column and Row

- `flex-direction : column` 일 때 main axis와 cross axis는 **반대!!**
- main axis = column
- cross axis = row

- 그러므로 `justify-content`는 **main axis**(세로) 이고, `align-items`는 **cross axis**(가로) 이다.

<br/><br/><br/><br/><br/>

## 1.4 align-self and order

- 부모가 아닌 **자식**아이템의 위치를 직접 변경하고 싶을 때는 `align-self` 와 `order`을 사용

  (단, 부모의 높이가 설정되어 있어야 함.)

  <br/><br/>

#### 1. align-self

- align-item과 같이 동작, cross axis 방향에 있는 item의 위치를 바꿈

  ```css
  .child:nth-child(2) {
    align-self: center;
  }
  ```

  <br/><br/>

#### 2. order

- 순서를 바꿈, HTML을 통해 순서를 바꾸기 힘들 때 사용하면 좋음

- default 는 0이고 숫자가 작은순서대로 정렬됨.

  ex) order:1 로 주면 기본값이 0인 애들보다 뒤에 위치하게 됨.

<br/><br/><br/><br/><br/>

## 1.5 wrap, nowrap, reverse, align-content

- father과 child 모두 flex로 해주면 width값을 설정해줬더라도 한 줄로 됨

#### flex-wrap

- flex-wrap: wrap : child의 width 유지
- flex-wrap: nowrap : child를 모두 한줄로, default 값

#### reverse

- flex-direction: row-reverse : 오른쪽에서부터 1이 시작
- flex-direction: column-reverse : 오른쪽에서부터 1이 시작 (세로로)
- flex-wrap: wrap-reverse

<br/><br/><br/><br/><br/>

## 1.6 flex-grow, flex-shrink

- flex로 나열된 block들의 특정 child를 줄이거나(shrink) 늘려줌(grow)

#### flex-shrink

- 기본 값 : 1
- `flex-shrink: 2;` 이렇게 설정하면 화면을 줄였을 때, 2배로 줄어들음

### flex-grow

- 기본 값 : 0
- `flex-grow: 1;` : 빈 공간을 없애고 남은 공간을 가져감

<br/><br/><br/><br/><br/>

## 1.7 flex-basis

- flex-basis : initial size로 flex-grow를 설정하면 flex-basis가 무너진다.
- width로 대체될 수 있음, 잘 쓰이지는 않음

<br/><br/><br/><br/><br/>

## 2.2 CSS Grid Basic Concepts

- grid의 디자인은 parent요소에서 함 `display : grid` 로 적용
- `grid-template-columns : 250px 250px 250px;` -> 250px짜리 그리드가 세개 생김
- `grid-template-rows: 100px 50px 300px;` -> 지정한 픽셀의 로우가 세개 생김
- `column-gap: 10px;` column 사이의 gap
- `row-gap: 10px;` row 사이의 gap

<br/><br/><br/><br/><br/>

## 2.3 Grid Template Areas

- `grid-template-rows: 100px repeat(2, 200px) 100px;` : repeat(반복할 개수, px)

- ```
   grid-template-areas:
    "header header header header"
    "content content . nav"
    "content content . nav"
    "footer footer footer footer"

  .header{
    background-color: #2ecc71;
    grid-area: header;
  }

  ```

  변수처럼 만들어 템플릿으로 사용할 수 있음

<br/><br/><br/><br/><br/>

## 2.4 Rows and Columns

- grid-column-start: 1; 시작

- grid-column-end:4; 끝(n-1로 생각하면 쉬움)

  -> column은 3칸 차지

- grid-row-start:2;

- grid-row-end:4;

  -> row는 2칸 차지

<br/><br/><br/><br/><br/>

## 2.5 Shortcuts

- grid-column:1/4; 3칸
- grid-column:span 4; 4칸
- grid-column: 2/span 2; 2번째부터 2칸

<br/><br/><br/><br/><br/>

## 2.6 Line Naming

- 이름을 붙여 사용하는 방법

  ```css
  grid-template-columns: [first-line] 100px [second-line] 100px [third-line] 100px [fourth-line] 100px [fifth-line] 100px;

  grid-template-rows: repeat(4, [row-line] 100px);

  .content {
    background-color: #3498db;
    grid-column: first-line/fourth-line;
    grid-row: row-line 2 / row-line 4;
  }
  ```

<br/><br/><br/><br/><br/>

## 2.7 Grid Template

- 부모요소

  ```css
  grid-template:
    [header-start] "header header header header" 1fr [header-end]
    [content-start] "content content content nav" 3fr [content-end]
    [footer-start] "footer footer footer footer" 1fr [footer-end] / 1fr 1fr 1fr 1fr;
  ```

- 자식요소

  ```css
  .header {
    background-color: #2ecc71;
    grid-area: header;
  }
  ```

- 이렇게 하면 width를 이 템플릿이 꽉 채울 수 있게 된다

<br/><br/><br/><br/><br/>

## 2.8 Place Items

- `justify-items` , `align-items`로 그리드 채우는 것 설정 , default : stretch

- `place-items: y x`는 위 두 값 통합

  ex) ` place-items: stretch center;`

<br/><br/><br/><br/><br/>

## 2.9 Place Content

- justify-content : 그리드의 가로 정렬, default 는 start

- align-content : 그리드의 세로정렬

  둘 다 start, end, space-evenly, space-around, space-between사용

- place-content: 수직,수평

<br/><br/><br/><br/><br/>

## 2.10 Auto Columns and Rows

- justify-self: 자식요소에서의 가로정렬
- align-self: 자식요소에서의 세로정렬
- place-self: 가로,세로 정렬

---

#### 중요

- grid-auto-flow: row|column|row dense| column dense
  - 자동으로 row|column을 채움, dense : 작은 크기의 아이템이 나타나면 걔를 먼저 채움(접근성 떨어짐)
- grid-auto-columns | grid-auto-rows : 자동으로 생성된 그리드 트랙의 크기를 지정한다

<br/><br/><br/><br/><br/>

## 2.11 minmax

> 최소, 최대값을 정할 수 있음

```css
grid-template-columns: repeat(4, minmax(100px, 150px));
```

- minmax(min값, max값)

<br/><br/><br/><br/><br/>

## 2.12 auto-fit auto-fill

![image](https://user-images.githubusercontent.com/51187540/115475777-5b37e900-a27b-11eb-81a7-5a81616e929e.png)

- 위에가 autofill, 아래가 autofit

```css
.grid:first-child {
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}
.grid:last-child {
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
```

- autofill 자동으로 다른 요소들이 들어올 공간을 만듦
- autofit 개수에 맞게 채움

<br/><br/><br/><br/><br/>

## 2.13 min-content max-content

```css
grid-template-columns: repeat(auto-fill, minmax(min-content, 1fr));
```

- min-content 최소한의 크기를 가지게 해줌
- max-content 최대한의 크기를 가지게 해줌

<br/><br/><br/><br/><br/>

---

## 3.0 CSS Preprocessors and Set Up

- gulpfile.bable.js 의 scss 컴파일 방법 **(gulpfile.babel.js)**

- src에 있는 scss파일을 읽어서 dest로 지정한 경로에 css파일로 컴파일 해

  ```javascript
  const routes = {
    css: {
      watch: "src/scss/*",
      src: "src/scss/styles.scss", 
      dest: "dist/css",
    },
  };
  ```

  

- 파일 전체 내용

  ```javascript
  import gulp from "gulp";
  import del from "del";
  import sass from "gulp-sass";
  import minify from "gulp-csso";
  import autoprefixer from "gulp-autoprefixer";
  
  sass.compiler = require("node-sass");
  
  const routes = {
    css: {
      watch: "src/scss/*",
      src: "src/scss/styles.scss", 
      dest: "dist/css",
    },
  };
  
  const styles = () =>
    gulp
      .src(routes.css.src)
      .pipe(sass().on("error", sass.logError))
      .pipe(
        autoprefixer({
          flexbox: true,
          grid: "autoplace",
        })
      )
      .pipe(minify())
      .pipe(gulp.dest(routes.css.dest));
  
  const watch = () => {
    gulp.watch(routes.css.watch, styles);
  };
  
  const clean = () => del(["dist/"]);
  
  const prepare = gulp.series([clean]);
  
  const assets = gulp.series([styles]);
  
  const live = gulp.parallel([watch]);
  
  export const dev = gulp.series([prepare, assets, live]);
  
  ```

  

<br/><br/><br/><br/><br/>

## 3.1 Variables and Nesting

### Variables

- 파일명에 ```_```를 붙이면 scss만을 위한 파일이 된다. (compile되지 않음)

  ```_variables.scss```

- **변수 설정** : 앞에 ```$```를 붙여서 설정한다.

  - _variables.scss

  ```scss
  $bg: #e7473c;
  $title: 32px;
  ```

  <br/>

- style.scss 에서 **import** : @import 파일명

  ```scss
  @import "_variables";
  body {
    background: $bg;
  }
  ```

<br/>

<br/>

### Nesting

- 하위 요소의 속성을 지정할 수 있음

- 예시 css

  ```scss
  .box {
    margin-top: 20px;
  }
  
  .box:hover {
    background-color: green;
  }
  
  .box h2 {
    color: blue;
  }
  
  .box button {
    color: red;
  }
  
  ```

- 예시 scss

  ```scss
  .box{
    margin-top: 20px;
    &:hover{
      background-color: green;
    }
    h2{
    	color: blue;
    }
    button{
    	color: red;
    }
  }
  ```

  

