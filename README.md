# Brick Breaker (벽돌깨기)

Canvas API를 사용하여 만든 브라우저 기반 벽돌깨기 게임입니다. 
방향키 또는 마우스를 이용해 패들을 조작하여 공을 튕기고, 모든 벽돌을 제거하면 승리합니다.

![screenshot](./assets/bg.jpeg)

## 🛠 주요 기능

- 캔버스를 이용한 게임 UI 구성
- 키보드 및 마우스 조작 지원
- 충돌 감지 (공 ↔ 벽돌, 공 ↔ 패들)
- 점수, 목숨 시스템
- 승리 및 실패 알림
- 게임 자동 초기화

## 🎮 게임 방법

- 방향키(←, →) 또는 마우스로 패들을 좌우로 조작합니다.
- 공이 벽돌에 닿으면 벽돌이 사라지고 점수가 올라갑니다.
- 모든 벽돌을 제거하면 **승리**, 공이 바닥에 닿으면 **목숨 -1**
- 목숨이 모두 소진되면 **게임 오버**

## ⚙ 설정 값 (script.js 내 `data` 객체)

```js
const data = {
  lives: 5,
  speed: 2,
  paddleHeight: 10,
  paddleWidth: 75,
  bg: "./assets/bg.jpeg",
  ballColor: "#04BF55",
  paddleColor: "#05AFF2",
  fontColor: "#F2BB16",
  brickStartColor: "#F29F05",
  brickEndColor: "#F21905",
  brickRow: 3,
  brickCol: 5,
  brickWidth: 75,
  brickHeight: 20,
  brickPad: 10,
  brickPosX: 30,
  brickPosY: 30,
};
```

- 위와 같이 옵션화를 하여 게임을 조금 더 다양한 상황으로 만들어볼 수 있습니다.

## 🧱 벽돌 충돌 감지 예시

```js
detectCollision = () => {
  let currentBrick = {};

  for (let colIndex = 0; colIndex < this.brickCol; colIndex++) {
    for (let rowIndex = 0; rowIndex < this.brickRow; rowIndex++) {
      currentBrick = this.bricks[colIndex][rowIndex];

      if (1 !== currentBrick.status) {
        continue;
      }

      if (
        this.ballX > currentBrick.x &&
        this.ballX < currentBrick.x + this.brickWidth &&
        this.ballY > currentBrick.y &&
        this.ballY < currentBrick.y + this.brickHeight
      ) {
        this.directY = -this.directY;
        currentBrick.status = 0;
        this.score++;
      }
    }
  }
};
```

## 🔗 참고 자료

- [MDN - 2D 벽돌깨기 튜토리얼](https://developer.mozilla.org/en-US/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript)

## 💻 실행 방법

```bash
# 로컬 서버에서 실행 (VSCode Live Server 추천)
index.html 열기
```
