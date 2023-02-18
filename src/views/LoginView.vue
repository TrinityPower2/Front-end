<template>
  <div id="formbox">
    <h1>Authentication</h1>
    <div class="form" id="loginform" v-if="loginscreen">
      <input v-model="email" placeholder="E-mail">
      <input v-model="password" placeholder="Password">
      <button @click="()=>login()">LOGIN</button>
      <a @click="()=>{loginscreen=false}">No account ?</a>
    </div>
    <div class="form" id="registerform" v-if="!loginscreen">
      <input v-model="name" placeholder="Username">
      <input v-model="email" placeholder="Email">
      <input v-model="password" placeholder="Password">
      <input v-model="repassword" placeholder="Confirm Password">
      <div v-if="!matching">Password don't match</div>
      <button @click="()=>register()">LOGIN</button>
      <a @click="()=>{loginscreen=true}">Already an account ?</a>
    </div>
    
  </div>
</template>

<style scoped>
    #formbox{
        margin: auto;
        margin-top: 20vh;
        justify-content: center;
        border-radius: 5vh;
        height: 50vh;
        width: 40vw;
        background-color: slategrey;
    }

    .form{
      display: flex;
      flex-direction: column;
    }

    input{
      width: 20vw;
      margin: auto;
      margin-top: 2vh;
    }

    button{
      width: 20vw;
      height: 5vh;
      margin: auto;
      font-size: larger;
      margin-top: 5vh;
    }

    a{
      margin-top: 2vh;
    }
</style>

<script>
export default {
    name:'LoginView',
    data(){
      return{
        //True : login / False : register
        loginscreen: true,
        name: "",
        email: "",
        password: "",
        repassword: "",
        matching: true
      }
    },
    methods:{
      login(){
        fetch("api/api/auth/login", 
        {method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({email:this.email,password:this.password})})
        .then((response)=>{
          if (response.ok) {
            return response.json();
          }
          throw new Error('Something went wrong');
        })
        .then((parsed) => {localStorage.setItem('token',parsed.token)})
        .then(()=>{this.$router.push('/calendar');})
        .catch(()=>{alert("Login Failed")}) //Essayer de faire un système où on affiche l'erreur exact à l'user
      },

      register(){

        if(this.password===this.repassword){
          fetch("api/api/auth/register", 
          {method: 'POST',
          headers: {
              'Content-Type': 'application/json'
          },
          body: JSON.stringify({name:this.name,email:this.email,password:this.password})})
          .then((response)=>{
            if (response.ok) {
              return response.json();
            }
            throw new Error('Something went wrong');
          })
          .then((parsed) => {localStorage.setItem('token',parsed.token)})
          .then(()=>{this.$router.push('/calendar');})
          .catch(()=>{alert("Registration Failed")})  
        }
        else{
          this.matching = false
        }
      }

    }

}
</script>

