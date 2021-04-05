

# (s)css-layout-master



>css layout master study
>
><p style="font-size:8px">https://nomadcoders.co/css-layout-masterclass</p>







## 목차



- [1.1 First Rule of Flexbox](#11-First-Rule-of-Flexbox)
- [1.2 Main Axis and Cross Axis](#12-Main-Axis-and-Cross-Axis)
- [1.3 Column and Row](13-Column-and-Row)
- [1.4 align-self and order](14-align-self-and-order)



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

  - stretch :  wrapper에 맞게 늘림(단 children의 height이 없어야 함)
  
  - flex-start : 처음에 맞춤

<br/><br/><br/><br/><br/>

## 1.3 Column and Row

- ```flex-direction : column``` 일 때 main axis와 cross axis는 **반대!!**
- main axis = column
- cross axis = row

- 그러므로 ```justify-content```는 **main axis**(세로) 이고, ```align-items```는 **cross axis**(가로) 이다.

<br/><br/><br/><br/><br/>

## 1.4 align-self and order

- 부모가 아닌 **자식**아이템의 위치를 직접 변경하고 싶을 때는 ```align-self``` 와 ```order```을 사용

  (단, 부모의 높이가 설정되어 있어야 함.)

  <br/><br/>

#### 1. align-self

- align-item과 같이 동작, cross axis 방향에 있는 item의 위치를 바꿈 

  ```css
  .child:nth-child(2){
    align-self: center;
  }
  ```

  <br/><br/>

#### 2. order

- 순서를 바꿈, HTML을 통해 순서를 바꾸기 힘들 때 사용하면 좋음

- default 는 0이고 숫자가 작은순서대로 정렬됨.

  ex) order:1 로 주면 기본값이 0인 애들보다 뒤에 위치하게 됨.