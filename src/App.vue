<template>
  <div class="app">
    <Board v-bind:timers="timers" v-bind:addTimer="addTimer"/>
  </div>
</template>

<script>
import Board from "@/components/Board.vue";
import timer from "@/components/Timer.vue";

export default {
  computed: {
    timer() {
      return timer
    }
  },
  components: {Board},
  data() {
    return {}
  },
}
</script>

<style>
@font-face {
  font-family: "Gotham Pro";
  src: url("./../public/shrift/gothampro.woff2") format("woff2"),
  url("./../public/shrift/gothampro.woff") format("woff");
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}

* {
  font-family: "Gotham Pro";
  margin: 0;
  padding: 0;
  background-color: #353638;
  box-sizing: border-box;
}

.app {
  max-width: 1100px;
  margin: 0 auto;
}
</style>