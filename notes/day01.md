# Day01

> Basic usage of canvas

- `<canvas></canvas>` default 크기 : 300px \* 150px
- `<canvas></canvas>`
  - two attributes : `height`, `width`
  - 랜더링 왜곡: X css O element attributes
  - Canvas가 지원 되지 않는 브라우저는 **Fallback Content**를 사용해야한다.

```html
<canvas id="clock" width="150" height="150">
  <img src="images/clock.png" width="150" height="150" alt="" />
</canvas>
```

---

`<canvas>` 지원 여부 체크하기

```js
const canvas = document.getElementById("canvas");
// Checking for support

if (canvas.getContext) {
  const ctx = canvas.getContext("2d");
  // drawing Code
} else {
  // canvas-unsupported code here
  alert("Canvas unsupported !");
}
```

## Drawing shapes with canvas

- Drawing Rectangle

  - `fillRect(x, y, width, height)` (채운 직사각형)
  - `strokeRect(x, y, width, height)` (외곽선만 채운 직사각형)
  - `clearRect(x, y, width, height)` (지정영역만큼 지우기 - 사각형모양)

- Drawing paths

  - `beginPath()` (새로운 path 을 생성)
    - 기존의 path를 초기화
    - 호출 후에 항상 `moveTo()`를 작성해야한다.
  - `closePath()` (현재 지점 - path의 시작부분 선 긋기)
    - 단, 이미 도형이 채워져있거나 시작점과 같은 위치에 있으면 동작 X
    - `fill()` 호출 한다면 자동으로 `closePath()` 호출
    - `stroke()` 호출시 `closePath()` 선언 필요
  - `stroke()` (도형을 그릴때 외곽선만 채우기)
  - `fill()` (도형을 그릴때 색 채우기)

- Moving the pen

  - `moveTo(x, y)` : 시작 포인트를 변경

- Lines

  - `lineTo(x, y)` : x, y는 선의 end point, 이전 path의 end point는 start point로 된다. 즉 start point - end point를 잇는 직선을 그려준다.
    - `moveTo(x, y)`로 start point가 변경될 수 있다.

- Arcs

  - `arc(x, y, radius, startAngle, endAngle, counterclockwise)`
    - `x, y`는 호의 중심
    - `radius`는 반지름
    - `startAngle` `endAngle` 호의 각도
    - `counterclockwise` : 기본값 `false`(시계방향), `true`(반시계 방향)
  - `arcTo(x1, y1, x2, y2, radius)`

- Bezier and quadratic curves

  - [Bézier curves](https://developer.mozilla.org/en-US/docs/Glossary/Bezier_curve)

- Rectangles
  - `rect(x, y, width, height)`
    - 이 메소드를 실행 전에 `moveTo(x, y)`를 자동으로 호출한다.
    - 즉, `moveTo(x, y)`를 선언 할 필요가 없다.

---

## Path2D objects

> 경로를 빠르게 구현하는 방법

```js
new Path2D(); // 비어있는 path 객체 생성
new Path2D(path); // 다른 path2D를 복사
```

- `Path2D` Object은 path method를 이용할수 있다.
  - ex) Path2D.rect();
- `Path2D.addPath(path, [.,transform])` path2D에 path를 추가한다.(자식처럼..)
