<template>
  <SiteHeader/>
  <div class="about">
    <h1>This is an about page</h1>
    <input v-model="name">
    <button @click="()=>fetchtext()">Button</button>
  </div>
</template>

<script>
import SiteHeader from '@/components/SiteHeader.vue'

export default {
  name: 'AboutView',
  components: {
    SiteHeader
  },
  methods:{
    startGame(type){
      this.$router.push('/game/'+type);
    },
    data(){
      return{
        //The following variable is used to update the keys of the ScoreBoard Components to make them rerender when logging in.
        name: ""
      }
    },
    fetchtext(){
      fetch("api/ping/"+this.name)
      .then((response)=>{return(response.json())})
      .then((parsed) => {alert("We know its you who pressed the button ! " + parsed.message + " !")})
    }
}
}
</script>