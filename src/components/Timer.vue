<template>
  <div class="timer" v-bind:class="{disable: isNotStart}">
    <div class="currentTime">
      {{this.currentHour !== 0 ? this.currentHour + ':' : '' }}{{(this.currentHour === 0 && this.currentMin === 0) ? '' : this.currentMin + ':' }}{{currentSec}}
    </div>
    <hr class="line">
    <div class="buttons">
      <button v-if="isNotStart" @click="startTimer">
        пуск
      </button>
      <button v-else @click="pauseTimer">
        пауза
      </button>
      <button @click="stopTimer">
        стоп
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSec: 0,
      currentMin: 0,
      currentHour: 0,
      isNotStart: true,
      idIntervals: 0,
    }
  },
  methods: {
    incTime() {
      if (this.currentSec === 59 && this.currentMin === 59) {
        this.currentSec = 0;
        this.currentMin = 0;
        this.currentHour++;
      } else if (this.currentSec === 59) {
        this.currentSec = 0;
        this.currentMin++;
      } else {
        this.currentSec++;
      }
    },
    clearTime() {
      this.currentMin = 0;
      this.currentSec = 0;
      this.currentHour = 0;
    },
    startTimer() {
      this.isNotStart = false;
      this.idIntervals = setInterval(this.incTime, 1000);
    },
    stopTimer() {
      this.clearTime();
      clearInterval(this.idIntervals);
      this.isNotStart = true;
    },
    pauseTimer() {
      this.isNotStart = true;
      clearInterval(this.idIntervals);
    }
  }
}
</script>

<style scoped>
.timer {
  max-width: 100%;
  background-color: #9E9E9E;
}

.line {
}

.currentTime {
  background-color: #9E9E9E;
  padding: 20px 0px;
  font-style: normal;
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  text-align: center;
  color: white;
}

.buttons {
  background-color: #9E9E9E;
  padding: 20px 0px;
  text-align: center;
}

.buttons button {
  padding: 10px;
  font-size: 14px;
  border: 1px solid black;
  cursor: pointer;
  background-color: #9E9E9E;
}

.buttons button:not(:last-child) {
  margin-right: 48px;
}

.buttons button:hover {
  background-color: #353638;
  color: white;
}

.disable {
  opacity: 0.6;
}
</style>