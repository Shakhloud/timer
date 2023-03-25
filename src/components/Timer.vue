<template>
  <div class="timer" v-bind:class="{disable: isNotStart}">
    <div class="currentTime">
      {{
        this.currentHour !== 0 ? this.currentHour + ':' : ''
      }}{{ (this.currentHour === 0 && this.currentMin === 0) ? '' : this.currentMin + ':' }}{{ currentSec }}
    </div>
    <hr class="line">
    <div class="buttons">
      <button class="startBtn" v-if="isNotStart" @click="startTimer">
      </button>
      <button class="pauseBtn" v-else @click="pauseTimer">
      </button>
      <button class="stopBtn" @click="stopTimer">
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
  margin: 0 auto;
  width: 225px;
  background-color: #9E9E9E;
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
  font-size: 14px;
  cursor: pointer;
  background-color: #9E9E9E;
  border: none;
}

.buttons button img {
  width: 20px;
  height: 20px;
}

.buttons button:not(:last-child) {
  margin-right: 48px;
}

.disable {
  opacity: 0.6;
}

.startBtn {
  width: 20px;
  height: 20px;
  background: url("./../../public/start.svg") no-repeat;
}

.pauseBtn {
  width: 20px;
  height: 20px;
  background: url("./../../public/pause.svg") no-repeat;
}

.stopBtn {
  width: 20px;
  height: 20px;
  background: url("./../../public/stop.png") no-repeat;
}

@media (max-width: 1024px) {
  .timer {
    margin: 0 auto;
    width: 280px;
    background-color: #9E9E9E;
  }
}

@media (max-width: 768px) {
  .timer {
    width: 320px;
  }
}
</style>