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
