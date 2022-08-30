<template>
  <h1>{{ customMsg }}</h1>
  <p>This is a simple example of a Vue.js component.</p>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>
  <button @click="increase">+1</button>
  <button @click="decrease">-1</button>
</template>

<script>
export default {
  props: {
    msg: {
      type: String,
      default: "Hello World!",
      validate: (value) => {
        return value.length > 0;
      },
    },
    start: {
      type: Number,
      required: true,
      default: 1,
      validate: (value) => {
        return value > 0;
      },
      status: {
        type: String,
        default: "success",
        validate: (value) => {
          return ["success", "warning", "danger"].includes(value);
        },
      },
    },
  },
  data() {
    return {
      counter: 5,
    };
  },
  methods: {
    increase() {
      this.counter++;
    },
    decrease() {
      this.counter--;
    },
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customMsg() {
      return this.msg || "Hello World!";
    },
  },
};
</script>

<style>
button {
  background-color: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 15px;
  transition: 0.3s ease-in-out;
}
button:hover {
  background-color: #5aa67b;
  transition: 0.3s ease-in-out;
}
</style>
