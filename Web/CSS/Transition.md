# Transition

## 정의

- 속성을 서서히 변화시키는 속성

```css
transition: property timing-function duration delay
```



## 속성

### property

- 적용시킬 속성을 정한다
  - 모든 속성을 적용시킬수 있지만, 변화를 하고픈 속성만 정할 수있다.
  - 예를 들어 넓이와 배경색만 바꾸는 것만 적용시킬 수 있다는 것이다.

### timing-function

- 진행 속도
  - cubic-bezier를 잘 사용하자.

### duration

- 끝날때까지 걸리는 시간을 정한다.

### delay

- transition이 시작하는 시간을 연기할 수 있다.