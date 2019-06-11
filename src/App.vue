<template>
  <div id="app">
    <h1>Test</h1>
    <button v-custom-on:click="clicked">Click Me!</button>
    <div
      v-custom-on:mouseenter="boxEntered"
      v-custom-on:mouseleave="boxLeft"
      style="width: 100px; height: 100px; background-color: lightgreen"
    >
      Enter this box!
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  directives: {
    customOn: {
      bind(el, binding) {
        // el.onclick = function() {
        //   binding.value();
        // };
        const type = binding.arg;
        el.addEventListener(type, binding.value);
      }
    }
  },
  methods: {
    clicked() {
      alert("I was clicked!");
    },
    boxEntered() {
      alert("Mouse is in green box!");
    },
    boxLeft() {
      console.log("Mouse left green box!");
    }
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
