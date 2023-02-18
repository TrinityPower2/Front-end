<template>
    <div id="list">
        <h2>Todo List</h2>
        <ul>
            <li v-for="task in tasks" v-bind:key="task.id" >{{ task.title }}</li>
        </ul>
        <h4>New Task:</h4>
        <input v-model="newTitle"/>
        <input v-model="newDesc"/>
        <button @click="()=>addTask()">ADD</button>
    </div>
</template>

<script>
export default {
    name:'TodoList',
    data(){
      return{
        //The following variable is used to update the keys of the ScoreBoard Components to make them rerender when logging in.
        tasks: [],
        isConnected: false,
        newTitle: "",
        newDesc:""
      }
    },
    beforeMount() {
        if(localStorage.getItem('token')){
            console.log(localStorage.getItem('token'));
            this.isConnected = true;
        }
        if(this.isConnected){
            localStorage.getItem("token");
            fetch("api/api/tasks", {headers: {'Authorization': 'Bearer '+ localStorage.getItem("token")}})
            .then((response)=>{return(response.json())})
            .then((parsed) => {this.tasks = parsed.tasks; console.log(this.tasks)})
        }
    },
    methods:{
        addTask(){
            fetch("api/api/tasks", 
            {method: 'POST',
            headers: {
                'Authorization': 'Bearer '+ localStorage.getItem("token"),
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({title:this.newTitle,description:this.newDesc})})
            .then((response)=>{return(response.json())})
            .then((parsed) => {this.tasks.push(parsed.task)})
            
    }
    }
}
</script>

<style>
    #list{
        max-width: 20vw;
        overflow-x: hidden;
        border: solid black 1px;
    }
</style>