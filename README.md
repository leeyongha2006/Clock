# Clock
JavaScript를 사용하여 시계 만들기
### 자바 스크립트를 이용해 현재 시간을 불러와 화면에 나타내주는 프로그램이다
![image](https://github.com/leeyongha2006/Clock/assets/126844590/a63876c5-6979-4f88-9bc6-e7e30142ae89)

## javascript
```javascript
const deg = 6; // 각도 변화량 (Degree change amount)

// HTML에서 ID를 통해 모든 시계 바늘 요소 가져오기 (Get all clock hand elements from HTML using IDs)
const hr = document.querySelector('#hr');
const mn = document.querySelector('#mn');
const sc = document.querySelector('#sc');

setInterval(() => {
  let day = new Date(); // 현재 날짜 및 시간 정보 얻기 (Get current date and time information)

  // 시계 바늘 각도 계산 (Calculate clock hand angles)
  let ms = day.getMilliseconds() * deg; // 밀리초 * 각도 변화량
  let hh = day.getHours() * 30; // 시针 각도 (Hour hand angle)
  let mm = day.getMinutes() * deg; // 분침 각도 (Minute hand angle)
  let ss = day.getSeconds() * deg + ms / 1000; // 초침 각도 (Second hand angle)

  // 시계 바늘 스타일 변경 (Change clock hand styles)
  hr.style.transform = `rotateZ(${(hh) + (mm / 12)}deg)`; // 시침 회전 (Rotate hour hand)
  mn.style.transform = `rotateZ(${mm}deg)`; // 분침 회전 (Rotate minute hand)
  sc.style.transform = `rotateZ(${ss}deg)`; // 초침 회전 (Rotate second hand)

}, 1); // 매 1밀리초마다 실행 (Execute every 1 millisecond)
```
## css
```css


* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: thistle;
    font-family: "sans";
  
  }
  
  @font-face {
    src: url("font/sans.ttf");
    font-family: "sans";
  }
  
  .heading {
    color: white;
    text-align: center;
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    padding: 100px;
    line-height: 3vh;
  }
  
  .clock {
    width: 350px;
    height: 350px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: url(../assets/clock.png);
    background-size: cover;
  }
  
  .clock:before {
    content: "";
    position: absolute;
    width: 15px;
    height: 15px;
    background: #fff;
    border-radius: 50%;
    z-index: 10000;
  }
  
  .clock .hour,
  .clock .min,
  .clock .sec {
    position: absolute;
}

.clock .hour,
.hr {
  width: 160px;
  height: 160px;
}

.clock .min,
.mn {
  width: 190px;
  height: 190px;
}

.clock .sec,
.sc {
  width: 230px;
  height: 230px;
}

.hr,
.mn,
.sc {
  display: flex;
  justify-content: center;
  /* align-items: center; */
  position: absolute;
  border-radius: 50%;
}

.hr:before {
  content: "";
  position: absolute;
  width: 6px;
  height: 80px;
  background: #bb86fc;
  z-index: 10;
  border-radius: 6px 6px 0 0;
}

.mn:before {
  content: "";
  position: absolute;
  width: 4px;
  height: 90px;
  background: #fff;
  z-index: 11;
  border-radius: 6px 6px 0 0;
}

.sc:before {
  content: "";
  position: absolute;
  width: 2px;
  height: 150px;
  background: #70efde;
  z-index: 12;
  border-radius: 6px 6px 0 0;
}
```
## index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Clock</title>
  <link rel="stylesheet" href="css/style.css" />
  <link rel="icon" href="assets/favicon.png">

</head>

<body>
  <h2 class="heading">
    Clock
  </h2>
  <div class="clock">
    <div class="hour">
      <div class="hr" id="hr"></div>
    </div>
    <div class="min">
      <div class="mn" id="mn"></div>
    </div>
    <div class="sec">
      <div class="sc" id="sc"></div>
    </div>
  </div>
```
