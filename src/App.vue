<template>
  <img src="@/assets/logo.png" alt="Cannot load image!" />
  <Counter />
  <Counter />
  <Counter />
</template>
 
<script>
import Counter from "@/components/Counter.vue";
export default {
  name: "App",
  components: {
    Counter,
  },
};
</script>
 
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background-color: #354a5e;
  color: #fff;
  border-radius: 8px;
 
  border: 1px solid white;
  margin: 0px 10px;
  cursor: pointer;
}
button:hover {
background: #42B884;
}
 
</style>