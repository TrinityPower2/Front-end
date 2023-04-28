import DarkLightMode from '@/components/DarkLightMode.vue';

<template>
  <div id="nav">
    <router-link to="/landing-page">Landing Page</router-link> |
    <router-link to="/login-page">Login Page</router-link> |
    <router-link to="/login-Fg-Pwd-page">Login Fg Pwd Page</router-link> |
    <router-link to="/register-page">Register Page</router-link> |
    <router-link to="/fgpassword-page">Forgot Pwd Page</router-link> |
    <router-link to="/reset-password-page">Reset Pwd Page</router-link> |
    <router-link to="/entry-form-page">Entry Form Page</router-link> |
    <router-link to="/entry-form1-page">Entry Form Page 1</router-link> |
    <router-link to="/todo-list-page">Todo List Page 1</router-link> |
    <router-link to="/create-calendar-page">Create Calendar Page 1</router-link> |
  </div>
  <!-- <HeaderLine></HeaderLine> -->
</template>

<script>
import HeaderLine from "../components/HeaderLine.vue";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    HeaderLine,
  },
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
