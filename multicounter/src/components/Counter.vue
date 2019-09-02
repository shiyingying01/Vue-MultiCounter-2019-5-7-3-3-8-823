<template>
  <div class="counter">
    <h1>{{msg}}</h1>
    <span>{{index}}:</span>&emsp;
    <button @click="add">+</button>&emsp;
    <span>{{count}}</span>&emsp;
    <button @click="sub">-</button>;
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: {
    msg: String,
    index: Number
  },

  data() {
    return {
      count: this.index
    };
  },
  methods: {
    //增加
    add() {
      this.count++;
      this.$emit("getSum", 1);
    },
    //减少
    sub() {
      this.count--;
      this.$emit("getSum", -1);
    }
  },
  created() {
    this.$emit("getSum", this.index);
  },

  destroyed() {
    this.$emit("getSum", -this.count);
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
