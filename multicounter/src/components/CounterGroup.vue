<template>
  <div class="CounterGroup">
    <h1>{{msg}}</h1>
    <span>{{index}}:</span>&emsp;
    <button @click="add">+</button>&emsp;
    <span>{{value}}</span>&emsp;
    <button @click="sub">-</button>;
  </div>
</template>

<script>
export default {
  name: "CounterGroup",
  props: {
    msg: String,
    index: Number,
    value: Number
  },

  data() {
    return {
      count: this.index
    };
  },
  methods: {
    //增加
    add() {
      this.$emit("update", { index: this.index + 1, value: this.value + 1 });
    },
    //减少
    sub() {
      this.$emit("update", { index: this.index - 1, value: this.value - 1 });
    }
    //
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
