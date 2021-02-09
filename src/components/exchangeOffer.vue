<template>
  <div class="exchange-offer">
    <div class="content">
      <div class="line"></div>
      <span class="title">Предложение обмена</span>
      <div class="info" v-if="!accepted">
        <span class="full-name">Romario Richardson</span>
        <span class="text"
          >Предлагает Вам<span class="colored"> обменяться </span
          >автомобилями</span
        >
      </div>
      <div class="info" v-else>
        <span class="text-accepted"
          >Укажите цену, которую хотите<br />доплатить за автомобиль</span
        >
        <input type="text" v-model="surcharge" />
      </div>
      <div class="buttons">
        <div class="btn accept" @click="doubleAccept()">
          <img :src="require('../assets/accept.svg')" />
          <span>{{ accepted ? "Подтвердить" : "Принять" }}</span>
        </div>
        <div class="btn" :class="{ decline: !accepted }">
          <img :src="require('../assets/close.svg')" />
          <span>{{ accepted ? "Закрыть" : "Отклонить" }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ExchangeOffer",
  data() {
    return {
      accepted: false,
      surcharge: 0,
    };
  },
  methods: {
    doubleAccept() {
      if (!this.accepted) return (this.accepted = true);
      // отправка на бек
    },
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
  src: url("~@/assets/Gilroy-Bold.ttf");
  font-weight: bold;
}

.exchange-offer {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  position: relative;

  .content {
    padding: 0 1.6666666667vw 1.6666666667vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    background: linear-gradient(
      270deg,
      rgba(8, 8, 8, 0.85) 15.87%,
      rgba(8, 8, 8, 0.5525) 100%
    );
    border-radius: 0.3125vw;
    font-family: Gilroy;
    font-weight: bold;
    color: #fff;
    overflow: hidden;
    position: relative;

    .line {
      background: rgba(0, 0, 0, 0.37);
      width: 100%;
      height: 1.09375vw;
      position: absolute;
      top: 0;
      left: 0;
    }

    .title {
      margin: 2.2916666667vw 0;
      font-size: 1.5625vw;
      text-align: center;
      position: relative;

      &::after {
        content: "";
        width: 2.4479166667vw;
        height: 0.2604166667vw;
        border-radius: 0.5729166667vw;
        background: linear-gradient(90deg, #9f2627 16.43%, #e43c3a 100%);
        position: absolute;
        top: 100%;
        left: 0;
      }
    }

    .info {
      width: 100%;
      font-size: 0.9375vw;

      & > span {
        display: block;
        text-align: center;
      }

      .text {
        font-weight: normal;
        margin-bottom: 2.7083333333vw;

        .colored {
          color: #ff5e62;
        }
      }

      input {
        box-sizing: border-box;
        padding: 0.78125vw;
        margin: 1.3541666667vw 0 2.3958333333vw 0;
        border: 0;
        border-radius: 0.1041666667vw;
        background-color: rgba(0, 0, 0, 0.49);
        width: 100%;
        font-family: Gilroy;
        font-weight: bold;
        font-size: 0.9375vw;
        color: white;
        text-align: center;
      }
    }

    .buttons {
      padding-top: 1.0416666667vw;
      display: flex;
      width: 100%;
      border-top: 1px solid rgba(255, 255, 255, 0.25);

      .btn {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        border-radius: 0.1041666667vw;
        background: rgba(255, 255, 255, 0.06);
        width: 9.21875vw;
        height: 2.34375vw;
        font-weight: normal;
        font-size: 0.9375vw;

        img {
          width: 0.6770833333vw;
        }

        &.accept {
          background: linear-gradient(45deg, #52ff00 0%, #238600 100%);
          margin-right: 0.8333333333vw;

          &:hover {
            box-shadow: 0px 0.3125vw 0.8854166667vw rgba(82, 255, 0, 0.25);
          }

          img {
            width: 0.8854166667vw;
          }
        }

        &.decline {
          background: linear-gradient(90deg, #9f2627 16.43%, #e43c3a 100%);

          &:hover {
            box-shadow: 0px 0.3125vw 0.8854166667vw rgba(255, 0, 0, 0.25);
          }
        }
      }
    }
  }
}
</style>