<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <br />
    <input v-model="countNum" />
    <Counter v-for="n in getNum()"
     v-bind:key="n" 
     v-bind:index="n" 
     v-on:getSum="count"
     />
    {{sum}}
  </div>
</template>

<script>
import Counter from "./components/Counter.vue";

export default {
  name: "app",
  data() {
    return {
      countNum: 0,
      sum:0
    };
  },
  methods: {
    getNum: function() {
      if (this.isNumber(this.countNum)) {
        return parseInt(this.countNum);
      } else {
        return 0;
      }
    },

    isNumber: function(n) {
      return !isNaN(parseFloat(n) && isFinite(n));
    },

    count: function(e) {
      this.sum = this.sum + e;
    }
  },
  components: {
    Counter
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
