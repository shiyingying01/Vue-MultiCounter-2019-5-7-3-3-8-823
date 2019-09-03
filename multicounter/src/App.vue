<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <br />
    <input v-model="countNum" v-on:changeInput="changeInput"/>
    <!-- <Counter v-for="n in getNum()"
     v-bind:key="n" 
     v-bind:index="n" 
     v-on:getSum="count"
    />-->
    <CounterGroup v-for="n in getNum()" v-bind:key="n" 
    v-bind:index="n" 
    v-bind:value="getNumByIndex(i)" 
    v-on:update="updateList" />
    {{getSum()}}
  </div>
</template>

<script>
//import Counter from "./components/Counter.vue";
import CounterGroup from "./components/CounterGroup.vue";

export default {
  name: "app",
  data() {
    return {
      countNum:0,
      inputNum: 0,
      sum:0,
      counts: []
    };
  },
  components: {
    CounterGroup
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

    updateList: function(param) {
      let oldCounter = this.counts;
      oldCounter[param.index] = param.value;
      this.counts = [];
      for (let i = 0; i<oldCounter.length;i++){
        this.counts.push(this.oldCounter[i]);
      }
    },

changeInput(){
      let inputNum = this.getNum();
      while (inputNum > this.counts.length) {
        this.counts.push(this.counts.length - 1);
      }
      while (inputNum < this.counts.length) {
        this.counts.pop();
      }
    },

    getNumByIndex(index){
      return this.counts[index-1];
    },

    getSum(){
      for(let i of this.counts){
        this.sum+=i;
      }
    }

    // count: function(e) {
    //   this.sum = this.sum + e;
    // }
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
