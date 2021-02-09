<template>
  <div class="kill-list">
    <div class="item" v-for="(item, index) in kills" :key="index">
      <div class="murder" :style="{ color: item.murder.color }">
        {{ item.murder.fullName }}
      </div>
      <img :src="require('../assets/skullHead.svg')" />
      <div class="victim" :style="{ color: item.victim.color }">
        {{ item.victim.fullName }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "KillList",
  data() {
    return {
      kills: [
        {
          murder: {
            fullName: "Josh Killa",
            color: "#D765FF",
          },
          victim: {
            fullName: "Josh Pchella",
            color: "#8CFF46",
          },
        },
        {
          murder: {
            fullName: "Max Stol",
            color: "#8CFF46",
          },
          victim: {
            fullName: "Dima Grib",
            color: "#D765FF",
          },
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@font-face {
  font-family: Gilroy;
  src: url("~@/assets/Gilroy-Bold.ttf");
  font-weight: bold;
}

.kill-list {
  display: flex;
  justify-content: flex-end;
  flex-direction: column-reverse;
  font-family: Gilroy;
  font-size: 0.7291666667vw;
  position: absolute;
  left: 1.5625vw;
  bottom: 17.7083333333vw;

  .item {
    padding: 0.4166666667vw;
    display: flex;
    align-items: center;
    width: max-content;
    background: linear-gradient(
      270deg,
      rgba(8, 8, 8, 0.85) 15.87%,
      rgba(8, 8, 8, 0.5525) 100%
    );
    border-radius: 0.3125vw;
    margin-top: 0.5208333333vw;

    img {
      display: block;
      margin: 0 0.5208333333vw;
      width: 1.6145833333vw;
      height: 0.9895833333vw;
    }
  }
}
</style>