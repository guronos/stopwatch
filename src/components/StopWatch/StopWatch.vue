<template>
  <div>
    <div class="block-watch">
      <div class="time-panel" :class="{ opacity: !timeRun }">
        <div class="hours" v-if="hours">{{ hours }}:</div>
        <div class="minutes" v-if="minutes">{{ minutes }}:</div>
        <div class="seconds">{{ seconds }}</div>
      </div>
      <div><hr :class="{ opacity: !timeRun }" /></div>
      <div class="control-panel" :class="{ opacity: !timeRun }">
        <div>
          <div
            class="btn-play"
            v-if="!timeRun"
            @click="startStopWatch(hours, minutes, seconds)"
          ></div>
          <div class="wrap-pause-btn" v-else @click="pauseTime">
            <div class="btn-pause"></div>
            <div class="btn-pause"></div>
          </div>
        </div>
        <div class="btn-stop" @click="stopTime"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "StopWatch",
  data() {
    return {
      hours: 0,
      minutes: 0,
      seconds: 0,
      timeRun: false,
      interval: null,
      startTime : '',
    };
  },
  methods: {    
    startStopWatch() {
      this.timeRun = true;
      this.startTime = Date.now()
      setTimeout(this.runTime, 0);
    },
    runTime(){
      let pastTense = Math.trunc((Date.now() - this.startTime) / 1000);
      this.seconds = pastTense % 60
      this.minutes = Math.trunc(pastTense / 60)
      this.hours = Math.trunc((pastTense / 60) / 60)
      this.interval = setTimeout(this.runTime, 0)
    },
    pauseTime() {
      this.timeRun = false;
      clearTimeout(this.interval);
    },
    stopTime() {
      this.timeRun = false;
      this.seconds = 0;
      this.minutes = 0;
      this.hours = 0;
      clearTimeout(this.interval);
    },
  },
};
</script>
<style scoped>
.block-watch {
  background: #696969;
  color: rgb(255, 255, 255);
  width: 225px;
  height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.control-panel,
.time-panel {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.opacity {
  opacity: 0.4;
}
.time-panel {
  font-style: normal;
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  text-align: center;
  padding: 22px 0 20px 0;
}
.btn-play {
  width: 0;
  height: 0;
  border-top: 9px solid transparent;
  border-left: 18px solid #ffffff;
  border-bottom: 9px solid transparent;
  margin: 20px 24px;
}
.btn-stop {
  width: 20px;
  height: 20px;
  background: #ffffff;
  margin: 20px 24px;
}
.btn-pause {
  margin: 20px 2px;
  width: 3px;
  height: 20px;
  background: #ffffff;
  display: inline-block;
}
.wrap-pause-btn {
  margin: 0 24px;
}
</style>
