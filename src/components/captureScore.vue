<template>
  <div class="capture-score">
    <div class="score">
      <div class="value">{{ gangs[0].score }}</div>
      <div class="time">
        <span class="timestamp">{{ time }}</span>
        <span>Время</span>
      </div>
      <div class="value">{{ gangs[1].score }}</div>
    </div>
    <div class="versus">
      <span :style="{ color: gangs[0].color }">{{ gangs[0].name }}</span>
      vs
      <span :style="{ color: gangs[1].color }">{{ gangs[1].name }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "CaptureScore",
  data() {
    return {
      interval: null,
      time: null,
      timestamp: Date.now(),
      gangs: [
        {
          name: "ballas",
          score: 19,
          color: "#D765FF",
        },
        {
          name: "families",
          score: 16,
          color: "#8CFF46",
        },
      ],
    };
  },
  mounted() {
    this.interval = setInterval(() => {
      this.time = new Date(
        Date.now() - new Date(this.timestamp)
      ).toLocaleTimeString([], { minute: "2-digit", second: "2-digit" });
    }, 1000);
  },
  beforeDestroy() {
    clearInterval(this.interval);
  },
};
</script>

<style lang="scss" scoped>
@font-face {
  font-family: Gilroy;
  src: url("~@/assets/Gilroy-SemiBold.ttf");
}

@font-face {
  font-family: Gilroy;
  src: url("~@/assets/Gilroy-Medium.ttf");
  font-weight: 300;
}

@font-face {
  font-family: Gilroy;
  src: url("~@/assets/Gilroy-Bold.ttf");
  font-weight: bold;
}

.capture-score {
  font-family: Gilroy;
  color: #fff;
  position: absolute;
  top: 1.3541666667vw;
  left: 50%;
  transform: translateX(-50%);

  .score {
    display: flex;
    background: linear-gradient(
      270deg,
      rgba(8, 8, 8, 0.85) 15.87%,
      rgba(8, 8, 8, 0.5525) 100%
    );
    border-radius: 0.3125vw;
    height: 3.125vw;

    .value {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 3.90625vw;
      font-weight: bold;
      font-size: 2.5vw;
    }

    .time {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      width: 3.3854166667vw;
      font-weight: 300;
      font-size: 0.625vw;
      background: rgba(0, 0, 0, 0.13);

      .timestamp {
        font-weight: normal;
        font-size: 0.7291666667vw;
        text-transform: uppercase;
      }
    }
  }

  .versus {
    padding: 0.3125vw;
    margin: 0.5208333333vw auto 0 auto;
    border-radius: 0.15625vw;
    width: max-content;
    background: linear-gradient(
      270deg,
      rgba(8, 8, 8, 0.85) 15.87%,
      rgba(8, 8, 8, 0.5525) 100%
    );
    font-weight: bold;
    font-size: 0.7291666667vw;
    text-transform: uppercase;
  }
}
</style>