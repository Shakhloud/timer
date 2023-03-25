<template>
  <div class="board">
    <div class="title"> Таймеры. Тестовое задание для компании "ООО Студия Беляевых"</div>
    <div class="timers">
      <div v-for="timer in timers">
        <Timer/>
      </div>
      <div>
        <button class="addTimer" @click="addTimer">
          +
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Timer from "@/components/Timer.vue";

export default {
  components: {Timer},
  data() {
    return {
      timerCount: 0,
      timers: []
    }
  },
  methods: {
    addTimer() {
      this.timers.push({id: Date.now()})
    }
  }
}
</script>

<style scoped>
.board {
  padding: 0px 20px;
}

.title {
  text-align: center;
  margin-top: 30px;
  font-size: 50px;
  font-weight: 700;
  color: white;
}

.timers {
  text-align: center;
  margin: 70px 0;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 45px 50px;
}

.timers div div {
  text-align: center;
}

.addTimer {
  padding: 43px 100px;
  background-color: #9E9E9E;
  color: white;
  font-size: 35px;
  border: none;
  opacity: 0.6;
  cursor: pointer;
  transition: 0.3s all ease;
}

.addTimer:hover {
  opacity: 0.9;
  transition: 0.3s all ease;
}

@media (max-width: 1024px) {
  .timers {
    grid-template-columns: 50% 50%;
    margin: 40px 0;
  }

  .title {
    font-size: 40px;
  }

  .addTimer {
    padding: 43px 130px;
  }
}

@media (max-width: 768px) {
  .timers {
    grid-template-columns: 100%;
    margin: 30px 0;
  }

  .title {
    font-size: 30px;
  }

  .addTimer {
    padding: 43px 149px;
  }
}
</style>