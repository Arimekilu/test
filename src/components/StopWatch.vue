<template>
  <div class="stopWatch" :class="{'off': !intervalWork, 'on' : intervalWork}">
    <div class="timeBlock">

      <span v-if="hour > 0">{{ hour }}:</span>
      <span v-if="min > 0">{{ min < 10 ? '0' + min : min }}:</span>
      <span>{{ sec < 10 ? '0' + sec : sec }}</span>
    </div>

    <div class="hr" :class="{'timerOnColor': intervalWork, 'timerOffColor': !intervalWork}"></div>


    <div class="btnBlock">
      <button v-on:click="startWatch" class="starBtn" v-if="!intervalWork">
        <img src="../assets/tryangle.svg" alt="" srcset="">
      </button>
      <button v-on:click="stopWatch" class="stopBtn" v-if="intervalWork">
        <img src="../assets/pauseOnStarted.svg" alt="" srcset="">
      </button>


      <button class="resetBtn" v-on:click="reset"
              :class="{'timerOnColor': intervalWork, 'timerOffColor': !intervalWork}"></button>
    </div>
  </div>
</template>

<script>
export default {

  name: 'StopWatch',
  data() {
    return {
      componentName: 'StopWatch',
      hour: 0,
      min: 0,
      sec: 0,
      intervalWork: false,
      timer: undefined,
      timerOnColor: '#FFFFFF',
      timerOffColor: '#9E9E9E'
    }
  },
  props: {},
  methods: {
    tick() {
      this.sec += 1
      if (this.sec >= 60) {
        this.sec = this.sec - 60
        this.min++
      }
      if (this.min >= 60) {
        this.hour++
        this.min = this.min - 60
      }
    },

    startWatch() {

      this.intervalWork = !this.intervalWork
      this.timer = setInterval(this.tick, 1000)

    },
    stopWatch() {
      this.intervalWork = !this.intervalWork
      clearInterval(this.timer)
    },
    reset() {
      this.stopWatch()
      this.intervalWork = false
      this.sec = 0
      this.min = 0
      this.hour = 0
    }

  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.stopWatch {
  box-sizing: border-box;
  height: 120px;
  width: 225px;
  background: rgba(105, 105, 105, 1);
  font-family: 'Gotham Pro', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  text-align: center;
  padding-top: 22px;
  margin-left: 50px;
  margin-bottom: 45px;
  /*transition: 300ms;*/
}

.timeBlock {

}

.hr {
  width: 100%;
  height: 1px;
  margin-top: 20px;
}

.btnBlock {
  margin-top: 20px;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.stopBtn {
  display: block;
  height: 20px;
  width: 20px;
  background: #696969;
  border: none;

}

.starBtn {
  display: block;
  width: 20px;
  height: 20px;
  background: #696969;
  border: none;
}

.resetBtn {
  display: block;
  width: 20px;
  height: 20px;

  border: none;
  margin-left: 48px;

}

.off {
  color: #9E9E9E;
}

.on {
  color: #FFFFFF;
}

.timerOnColor {
  background: #FFFFFF;
}

.timerOffColor {
  background: #9E9E9E;
}


</style>
