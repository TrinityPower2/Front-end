<template>
  <div class="home">
    <site-header/>
    <h1>WELCOME TO TIME 2 DO</h1>
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld v-if="false" msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import SiteHeader from '@/components/SiteHeader.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    SiteHeader
  }
}
</script>
