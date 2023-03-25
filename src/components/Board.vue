<template>
  <div>
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
.title {
  text-align: center;
  margin-top: 30px;
  font-size: 50px;
  font-weight: 700;
  color: white;
}

.timers {
  margin: 70px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 50px;
}

.addTimer {
  padding: 50px 133px;
  background-color: #9E9E9E;
  color: white;
  font-size: 35px;
  border: none;
  opacity: 0.6;
}
</style>