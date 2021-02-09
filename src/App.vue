<template>
  <div id="app">
    <capture-score />
    <kill-list />
    <exchange-offer />
  </div>
</template>

<script>
import CaptureScore from "./components/captureScore.vue";
import ExchangeOffer from "./components/exchangeOffer.vue";
import KillList from "./components/killList.vue";

export default {
  name: "App",
  components: { CaptureScore, KillList, ExchangeOffer },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  width: 100vw;
  height: 100vh;
  position: relative;
}
</style>
