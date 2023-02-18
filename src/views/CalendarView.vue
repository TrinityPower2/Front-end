<template>
  <SiteHeader/>
  <calendar v-if="false"/>
  <todo-list/>
</template>

<script>
import SiteHeader from '@/components/SiteHeader.vue';
import Calendar from '@/components/Calendar.vue';
import TodoList from '@/components/TodoList.vue';

export default {
    name:'CalendarView',
    components: { SiteHeader, Calendar, TodoList },
    beforeMount(){
      if(localStorage.getItem("token")){
            console.log(localStorage.getItem("token"));
            fetch('api/api/user', {
                headers: {
                'Content-Type': 'application/json',
                'authorization': 'Bearer '+ localStorage.getItem("token")
                }
            })
            .then((response)=>{
              if (response.ok) {
                return response.json();
              }
              throw new Error('Something went wrong');
            })
            .then((parsed) => {this.isConnected = true; this.userName = parsed.name})
            .catch(()=>{this.$router.push("/")})
        } else {
          this.$router.push("/");
        }
    }
}
</script>

<style>

</style>