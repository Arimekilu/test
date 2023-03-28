<template id="app">

  <StopWatch
      v-for="item in items"
      :key="item.message"
      :is="StopWatch">
  </StopWatch>

  <NewTimer v-on:click="newTimer"/>
</template>

<script>
import StopWatch from "@/components/StopWatch";
import NewTimer from "@/components/NewTimer";


export default {
  el: "#app",
  name: 'App',
  components: {
    StopWatch,
    NewTimer,
  },
  data() {
    return {
      items: []
    }
  },
  methods: {
    newTimer() {
      this.items.push(StopWatch)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  max-width: 1024px;
  margin-top: 72px;
  /*align-items: center;*/
  /*vertical-align: center;*/
}

@media (max-width: 1024px ) {
  #app {
    max-width: 1024px;

  }
}

@media (max-width: 768px ) {
  #app {
    max-width: 768px;

  }
}

@media (max-width: 320px ) {
  #app {
    max-width: 320px;
  }
}


</style>
