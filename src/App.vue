<template>
  <h2>Vue Forms and Data Binding</h2>
  <SignupForm />
</template>

<script>
import SignupForm from "./components/SignupForm.vue";

export default {
  name: "App",
  components: {
    SignupForm,
  },
  data() {
    return {};
  },
  methods: {},
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
body {
  margin: 0;
  background: #eee;
}
</style>
