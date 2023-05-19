<template>
    <body>
        <header>
            <div class="headernav">
                <div class="header-container">
                    <div class="header-image">
                        <img alt="Vue logo" src="../assets/TimeToDo1.png" class="VueLogo" />
                    </div>
                </div>
                <div class="Navbar">
                    <router-link to="/calendar-page" c class="to-page-nav">My Plannings</router-link>
                    <router-link to="/todo-list2-page" class="to-page-nav">My Todo Lists</router-link>
                    <router-link to="/create-calendar-page" class="to-page-nav">Create a Planning</router-link>
                </div>

                <router-link to="/todo-list-page" class="user"><font-awesome-icon icon="fa-solid fa-user-large"
                        style="--fa-primary-color: #411f51; --fa-secondary-color: #3d1f51" /></router-link>
                <div class="light">
                    <DarkLightMode></DarkLightMode>
                </div>
            </div>
        </header>
        <a id="top"></a>
        <div class="TodoPage-container">
            <div class="TodoLists-container">
                <div class="high-part-todo">
                    <div></div>
                    <h1 class="Todo-title">My Todo Lists</h1>
                    <font-awesome-icon @click ="()=>OpenList()" id="AddList" icon="fa-solid fa-plus" size="2xl" class="Plus-todo" />
                </div>
                <template v-for="(title,index) in ToDoList" :key="index">
                    <div class="Todolists-disp">    
                        <div class="Todolist-shape">
                            <div class="TodoList" >
                                    <div class="CloseTodoList-container">
                                        <button :id="'CloseTodoList-' + index" class="CloseTodoList" @click = "OpenDelete(title.name_todo)">x</button>
                                    </div>
                                    <div class="List-Title">{{title.name_todo}}</div>
                                <div class="Task" v-for="(task, taskIndex) in title.task" :key="taskIndex">
                                    <label :for="'checkbox-' + index + '-' + taskIndex" class="task-container">{{task.name_task}}
                                        <input type="checkbox" :id="'checkbox-' + index + '-' + taskIndex" :checked="task.is_done == 1" v-on:change="onCheckboxChange($event, task.id_task, title.id_todo)"/>
                                        <span :class="'checkmark checkmark-' + index + '-' + taskIndex"></span>
                                    </label>
                                    <label>{{ priority[task.priority_level-1] }}</label> 
                                </div>
                                <div class="button-container">
                                <button @click ="OpenTask(index)" type="submit" class="Task-add-btn" id="addBtn">
                                    Add Task
                                </button>
                                <button @click ="OpenUpdate(index)" type="submit" class="Task-update-btn" id="UpdateBtn">
                                    Update
                                </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- The Modal -->
                    <div  :id="'myModal' + index" class="modal">
                        <!-- Modal content -->
                        <div class="modal-content">
                            <span @click ="()=>CloseTask(index)" class="close">&times;</span>
                            <h1 class="modal-Title">{{title.name_todo}}</h1>
                            <div class="modal-center">
                                <div class="AddInputBox">
                                    <input type="text"  v-model = "NewTask" placeholder="Name Task" name="email" />
                                </div>
                                <div class="New-list-element">
                                    <div class="new-list-desc">
                                        Importance
                                    </div>
                                    <div class="custom-select">
                                        <select class="select-items" v-model="selectedImportance">
                                            <option value="0">Choose Importance :</option>
                                            <option value="1">Urgent</option>
                                            <option value="2">Important</option>
                                            <option value="3">Medium</option>
                                            <option value="4">Minor</option>
                                            <option value="5">Do Later</option>
                                        </select>
                                    </div>
                                </div>
                                <div class = "message" > {{message}}</div>
                                <div class="AddInputBox">
                                    <input @click ="()=>AddTask(title.name_todo)" type="submit" value="Add" name="submit" />
                                </div>
                            </div>
                        </div>
                    </div>
                </template>
                <div id="UpdateModal" class="modal1">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span @click ="()=>CloseUpdate()" class="close">&times;</span>
                        
                        <div class="modal-center1">
                                <input class="modal-Title-input" v-model= 'UpdateToDo.name_todo'  style="margin-bottom : 40px;"/>
                                <div class="New-list-element">
                                    <div class="new-list-desc" >
                                        Tasks
                                    </div>
                                    <div class="Add-another-task">
                                    <div v-for="(task, taskIndex) in UpdateToDo.task" :key="taskIndex" class ="new-task-create">
                                        
                                        <label class="task-container" style="margin-left: 0%;">
                                        <input type="checkbox"  :id="'checkbox-' + index + '-' + taskIndex" :checked="task.is_done == 1" v-on:change="onCheckboxChange($event, task.id_task, this.UpdateToDo.id_todo)"/>
                                        <span :class="'checkmark checkmark-' + index + '-' + taskIndex"></span>
                                        </label>
                                        <input type="text" v-model='task.name_task' class="new-task-input"/><br>
                                        <div class="CloseTask-container">
                                        <button :id="'CloseTask-' + index" class="CloseTask" @click = "OpenDeleteTask(task.name_task)">x</button>
                                        <div class="custom-select">  
                                        <select :id="'ImportanceTask-' + index" class="select-items" v-model="task.priority_level">
                                            <option value="0">Choose Importance :</option>
                                            <option value="1">Urgent</option>
                                            <option value="2">Important</option>
                                            <option value="3">Medium</option>
                                            <option value="4">Minor</option>
                                            <option value="5">Do Later</option>
                                        </select>
                                        </div>
                                        </div>
                                    </div>
                                    </div>
                                </div>
                        
                                <div class="New-list-element">
                                        <div class="new-list-desc">
                                            Add To Planner
                                        </div>
                                        <input type="datetime-local" class = "DescriptionInput" id="day" name="day-task" v-model = "selectedDate" min="2023-04-01" max="2028-12-31" @click = "resetCalendar()">
                                </div>
                                <div class="custom-select" v-show="selectedDate !== ''">
                                    <select class="select-items" v-model="selectedCalendar" id="Selected_Calendar" @click = 'GetEventByDateCalendar(selectedDate, selectedCalendar)'>
                                        <option value="0">Choose Calendar :</option>
                                        <option v-for="option in Calendar" :value="option.id_calendar" :key="option.id_calendar">{{ option.name_calendar }}</option>
                                    </select>
                                </div>
                                <div class="New-list-element"  v-show="selectedCalendar !== '0'">
                                    <div class="new-list-desc" >
                                        Duration
                                    </div>
                                    <div class="custom-select" id="Time-Task"  >
                                        <select v-model = "Duration" class="select-items" id="Duration_Task">
                                            <option value="0">Duration</option>
                                            <option value="1">1H00</option>
                                            <option value="2">2H00</option>
                                            <option value="3">3H00</option>
                                            <option value="4">4H00</option>
                                            <option value="5">5H00</option>
                                        </select>
                                    </div>
                            </div>
                            <div class="New-list-element"  v-show="selectedCalendar !== '0'">
                                    <div class="new-list-desc" >
                                        Importance
                                    </div>
                                <div class="custom-select">  
                                <select  class="select-items" v-model="priorityEvent">
                                    <option value="0">Choose Importance :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                                </div>
                            </div>
                            <div class = "message" > {{message}}</div>
                            <div style="width:65%; display:flex; justify-content:center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input @click ="()=>Update()" type="submit" value="Update" name="submit" />
                            </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div id="myModalDelete" class="modal">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span class="close" @click = 'CloseDelete'>&times;</span>
                        <h1 class="modal-Title">Delete Todo List</h1>
                        <div class="modal-center">
                            <p style="margin-top: 50px;">Are you sure you want to delete this List ?</p>
                            <div class = "message" > {{message}}</div>
                            <div class ="delete-list-button">
                            <div class="AddTaskInputBox no">
                                <input class="close" type="submit" value="Cancel" name="submit" @click = 'CloseDelete' />
                            </div>
                            <div class="AddTaskInputBox no">
                                <input style="margin-left: 0px;" type="submit" value="Delete" name="submit"  @click = 'DeleteToDo' />
                            </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div id="myModalDeleteTask" class="modal">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span class="close" @click = 'CloseDeleteTask'>&times;</span>
                        <h1 class="modal-Title">Delete Task</h1>
                        <div class="modal-center">
                            <p style="margin-top: 50px;">Are you sure you want to delete this Task ?</p>
                            <div class = "message" > {{message}}</div>
                            <div class ="delete-list-button">
                            <div class="AddTaskInputBox no">
                                <input class="close" type="submit" value="Cancel" name="submit" @click = 'CloseDeleteTask' />
                            </div>
                            <div class="AddTaskInputBox no">
                                <input style="margin-left: 0px;" type="submit" value="Delete" name="submit"  @click = 'DeleteTask' />
                            </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div id="NewListModal" class="modal1">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span @click ="()=>CloseList()" class="close">&times;</span>
                        <input type="text" class="modal-Title-input" v-model = "ToDo" placeholder="Name TodoList" style="margin-bottom : 40px;"/>
                        <div class = "message" > {{message}}</div>
                        <div class="modal-center1">
                            <div class="New-list-element">
                                <div class="new-list-desc">
                                    Tasks
                                </div>
                                
                                <div class="Add-another-task" >
                                    <div class="new-task-create">
                                    <label class="task-container" style="margin-left: 0%;">
                                    <input type="checkbox" v-model="taskChecked"/>
                                    <span class="checkmark"></span>
                                    </label>
                                    <input type="text" v-model="taskInput"  class="new-task-input" placeholder="..." /><br>
                                    <div class="custom-select">
                                        <select id="ImportanceTask" class="select-items" v-model="selectedImportance">
                                            <option value="0">Choose Importance :</option>
                                            <option value="1">Urgent</option>
                                            <option value="2">Important</option>
                                            <option value="3">Medium</option>
                                            <option value="4">Minor</option>
                                            <option value="5">Do Later</option>
                                        </select>
                                    </div>
                                    </div>
                               
                                <div v-for="(new_task, index) in AddTasks" :key="index" :id="'CloseTdTask-' + index" class="CloseTask-container">
                                    <button :id="'CloseTask-' + index" class="CloseTask" @click = "DeleteTdTask(index)">x</button>  
                                <div class="new-task-create">
                                    <label class="task-container" style="margin-left: 0%;">
                                    <input type="checkbox" :id="'taskChecked_' + index" v-model="taskCheckedArray[index]"/>
                                    <span class="checkmark"></span>
                                    </label>
                                    <input type="text" :id="'taskInput_' + index"  v-model="taskInputArray[index]" class="new-task-input" placeholder="..." /><br>
                                    <div class="custom-select">
                                        <select :id="'ImportanceTask-' + index" class="select-items" v-model="selectedImportanceArray[index]">
                                            <option value="0">Choose Importance :</option>
                                            <option value="1">Urgent</option>
                                            <option value="2">Important</option>
                                            <option value="3">Medium</option>
                                            <option value="4">Minor</option>
                                            <option value="5">Do Later</option>
                                        </select>
                                    </div>
                                    </div>
                                </div>
                                <div class="new-task-create" style="margin-top: 8px;">
                                    <font-awesome-icon icon="fa-solid fa-plus" size="s" @click="addTask()" />
                                    <p>New Task</p>
                                </div>
                            </div>
                            </div>
                                <div class="New-list-element">
                                        <div class="new-list-desc">
                                            Add To Planner
                                        </div>
                                        <input type="datetime-local" class = "DescriptionInput" id="day" name="day-task" v-model = "selectedDate" min="2023-04-01" max="2028-12-31" @click = "resetCalendar()">
                                </div>
                                <div class="custom-select" v-show="selectedDate !== ''">
                                    <select class="select-items" v-model="selectedCalendar" id="Selected_Calendar" @click = 'GetEventByDateCalendar(selectedDate, selectedCalendar)'>
                                        <option value="0">Choose Calendar :</option>
                                        <option v-for="option in Calendar" :value="option.id_calendar" :key="option.id_calendar">{{ option.name_calendar }}</option>
                                    </select>
                                </div>
                                <div class="New-list-element"  v-show="selectedCalendar !== '0'">
                                    <div class="new-list-desc">
                                        Duration
                                    </div>
                                    <div class="custom-select" id="Time-Task">
                                        <select v-model = "Duration" class="select-items" id="Duration_Task">
                                            <option value="0">Duration</option>
                                            <option value="1">1H00</option>
                                            <option value="2">2H00</option>
                                            <option value="3">3H00</option>
                                            <option value="4">4H00</option>
                                            <option value="5">5H00</option>
                                            
                                        </select>
                                    </div>
                                </div>           
                                <div class="New-list-element"  v-show="selectedCalendar !== '0'">
                                    <div class="new-list-desc" >
                                        Importance
                                    </div>
                                <div class="custom-select">  
                                <select  class="select-items" v-model="priorityEvent">
                                    <option value="0">Choose Importance :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                                </div>
                            </div>                 
                            <div style="width:65%; display:flex; justify-content:center; margin-top: 50px;">
                                <div class="AddTaskInputBox">
                                    <input @click ="()=>SubmitList()" type="submit" value="Add" name="submit" />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </div>
        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"></a>
        <footer>
            <div class="content-footer">
                <div class="top">
                    <div class="logo-details">
                        <img src="../assets/TimeToDo1.png" alt="LB logo" />
                        <p class="logo-name">
                            TIME TO DO <br />
                            <small>est. 2023</small>
                        </p>
                    </div>
                    <div class="media-icons">
                        <a href="https://www.linkedin.com/in/lou-brunesseaux-a843aa248"><font-awesome-icon
                                icon="fa-brands fa-linkedin-in" /></a>
                        <a href="mailto:loubruness@gmail.com"><font-awesome-icon icon="fa-brands fa-google" /></a>
                        <a href="https://github.com/loubruness"><font-awesome-icon icon="fa-brands fa-github" /></a>
                    </div>
                </div>
            </div>
        </footer>
    </body>
</template>

<script>
import DarkLightMode from "../components/DarkLightMode.vue";
export default {
    name: "TodoList2Page",
    components: {
        DarkLightMode,
    },
    data() {
        return{
        priority : ["Urgent", "Important", "Medium", "Minor", "Do Later"],
        selectedDate : '',
        selectedCalendar : "0",
        selectedEvent : "0",
        selectedImportance : "0",
        selectedImportanceArray : ["0"],
        taskInputArray : [''],
        taskInput : '',
        taskCheckedArray : [],
        NewTask : '',
        ToDo : '',
        Calendar : [],
        Events : [],
        ToDoList : [],
        UpdateToDo : [],
        TaskToDo : [],
        AddTasks : [],
        taskChecked : '',
        priorityEvent : '0',
        message : '',
        Duration : '0',
        DeleteName : '',
        DeleteTaskName : '',
        DeleteTaskIndex : '',
        OldTodo : '',
        createdEventId : '',
    
    
        }
    },
    methods : {
    /* This function is used for the + button in the NewListModal to add each time a new empty task*/
    addTask() {
      const newTask = {
        checked: false,
        inputText: "",
        importance : "0"
      };
     
      this.AddTasks.push(newTask);
      
    },
    /*This function is called each time a checkbox is checked/unchecked so that it will fetch in the db*/
    onCheckboxChange(event, taskIndex, todoIndex){

        const token = localStorage.getItem('token');

        const checkbox = event.target;
        const checked = (checkbox.checked ? 1 : 0)
        const selectedTask = this.ToDoList

        /*Finding the corresponding task that was checked/unchecked*/

        .find(todo => todo.id_todo === todoIndex)
        ?.task.find(task => task.id_task === taskIndex);
        selectedTask.is_done = checked;


        fetch("api/api/tasks/" + taskIndex, 
            {
                method: 'PATCH',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer ' + token
            },
            body: JSON.stringify({is_done: checked , id_todo : todoIndex})})
            .then((response)=>{    
                if (response.ok) {
                    return response.json();
                }
                else { 
                    
                    return response.json().then(error => {
                        throw new Error(JSON.stringify(error));
                });
            }})
            .catch((error) => {
                        let errorMessage;
                        try {
                            errorMessage = JSON.parse(error.message);
                        } catch {
                            errorMessage = {
                            message: 'An error occurred while processing your request.'
                            };
                        }
                        
                        console.log(errorMessage.message)
                        
                    });

    },
    /*All the functions Get are used in the initialized function to retrieve the database information*/
    async GetList() {
        const token = localStorage.getItem('token');

        try {
        const response = await fetch("api/api/todolist/", {
            method: 'GET',
            headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
            }
        });

        const data = await response.json();
        this.todos = JSON.parse(JSON.stringify(data.calendars));
        } catch (error) {
        console.error(error);
        }
    },

    async GetTask() {

        const token = localStorage.getItem('token');
        try {
        const response = await fetch("api/api/tasks", {
            method: 'GET',
            headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
            }
        });
        const data = await response.json();
        this.tasks = JSON.parse(JSON.stringify(data.list));
        } catch (error) {
        console.error(error);
        }
    },

    async GetCalendar() {
        const token = localStorage.getItem('token');

        try {
        const response = await fetch("api/api/calendar/", {
            method: 'GET',
            headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
            }
        });

        const data = await response.json();
        this.calendars = JSON.parse(JSON.stringify(data.calendars));
        } catch (error) {
        console.error(error);
        }
    },

    async GetEvent() {
        const token = localStorage.getItem('token');

        try {
        const response = await fetch("api/api/events", {
            method: 'GET',
            headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
            }
        });

        const data = await response.json();
        this.events = JSON.parse(JSON.stringify(data.list));
        } catch (error) {
        console.error(error);
        }
    },
    resetCalendar(){
        this.selectedEvent = "0";
        this.selectedCalendar = "0";
    },
    async GetEventByDateCalendar(date, calendar) {
       
        await this.GetEvent();
    
        this.Events = this.events
            .filter(event => event.id_calendar === calendar && event.start_date.split(" ")[0] === date)
            .map(event => {
                return {    
                    name_event: event.name_event,
                    id_event : event.id_event
                };
        });
    },
    async initializePage() {
        /*Initilialized the page by getting all the current to do list and tasks of the user*/
        await this.GetList();
        await this.GetTask();
        await this.GetCalendar();
        this.Calendar = this.calendars.map(calendar => {
            return {
                name_calendar: calendar.name_calendar,
                id_calendar : calendar.id_calendar,
            };
        })
       
        this.ToDoList = this.todos.map(todo => {
            return {
                name_todo: todo.name_todo,
                id_todo : todo.id_todo,
                task: this.tasks.filter(task => task.id_todo === todo.id_todo).map(task => {
                    return {
                    name_task: task.name_task,
                    description : "Description",
                    is_done: task.is_done,
                    priority_level : task.priority_level,
                    id_task : task.id_task
                    };
                })
            };
        })
    },
    OpenDelete(name){
        this.DeleteName = name;
        document.getElementById("myModalDelete").style.display = "block";
    },
    CloseDelete(){
        document.getElementById("myModalDelete").style.display = "none";
    },
    DeleteToDo(){

        const token = localStorage.getItem('token');

        fetch("api/api/todolist/fromname/" + this.DeleteName, 
          {
              method: 'DELETE',
          headers: {
              'Content-Type': 'application/json',
              'Authorization': 'Bearer ' + token
          },
        })
          .then((response)=>{    
            if (response.ok) {
              return response.json();
            }
            else { 
                  
                  return response.json().then(error => {
                      throw new Error(JSON.stringify(error));
              });
          }})
          .catch((error) => {
                      let errorMessage;
                      try {
                          errorMessage = JSON.parse(error.message);
                      } catch {
                          errorMessage = {
                          message: 'An error occurred while processing your request.'
                          };
                      }
                     
                    this.message = errorMessage.message;
                     
                      
                  });
        this.message = '';
        this.Reload();
    },
    DeleteTdTask(index){
        const closeTaskContainer = document.getElementById(`CloseTdTask-${index}`);
        closeTaskContainer.parentNode.removeChild(closeTaskContainer);
    },
    OpenDeleteTask(name){
  
        this.DeleteTaskName = name;
        document.getElementById("myModalDeleteTask").style.display = "block";
    },
    CloseDeleteTask(){
        document.getElementById("myModalDeleteTask").style.display = "none";
    },
    DeleteTask(){

        const token = localStorage.getItem('token');

        fetch("api/api/tasks/fromname/" + this.DeleteTaskName + "/" + this.UpdateToDo.name_todo, 
        {
            method: 'DELETE',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
        },
        })
        .then((response)=>{    
            if (response.ok) {
            return response.json();
            }
            else { 
                
                return response.json().then(error => {
                    throw new Error(JSON.stringify(error));
            });
        }})
        .catch((error) => {
                    let errorMessage;
                    try {
                        errorMessage = JSON.parse(error.message);
                    } catch {
                        errorMessage = {
                        message: 'An error occurred while processing your request.'
                        };
                    }
                    
                    this.message = errorMessage.message;
                    
                    
                });
        this.message = '';
        this.Reload();

    },
    AddTask(ToDo){
      
        const token = localStorage.getItem('token');
        if(this.NewTask == '' | this.selectedImportance == 0){
            this.message = 'You must fill all the required fields'
        }else
        {
        fetch("api/api/tasks/fromname", 
        {
            method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
        },
        body: JSON.stringify({name_task : this.NewTask, description:"Description", priority_level : this.selectedImportance, name_todo : ToDo})})
        .then((response)=>{    
            if (response.ok) {
            return response.json();
            }
            else { 
                
                return response.json().then(error => {
                    throw new Error(JSON.stringify(error));
            });
        }})
        .catch((error) => {
                    let errorMessage;
                    try {
                        errorMessage = JSON.parse(error.message);
                    } catch {
                        errorMessage = {
                        message: 'An error occurred while processing your request.'
                        };
                    }
                    
                    this.message = errorMessage.message;
                    
                    
                }); 
        this.message = '';
        this.Reload();
        }
    },
    async OpenUpdate(index){
        
        var UpdateToDoCopy = {...this.ToDoList[index]}
        this.UpdateToDo = JSON.parse(JSON.stringify(UpdateToDoCopy));
        document.getElementById("UpdateModal").style.display = "block";
        this.OldTodo = this.UpdateToDo.name_todo;
    },
    CloseUpdate(){
        this.message = '';
        this.selectedDate = '';
        this.selectedCalendar = '0';
        this.Duration = '';
        this.UpdateToDo = {};
        document.getElementById("UpdateModal").style.display = "none";
    },
    Update() {
    const token = localStorage.getItem('token');

    if (this.UpdateToDo.name_todo === '') {
        this.message = 'You must provide a To Do List Name';
    } else if (this.UpdateToDo.task.some(task => task.name_task === '' || task.priority_level === '0')) {
        this.message = 'You must fill all fields for the task';
    } else if(this.selectedDate !== '' && (this.selectedCalendar == "0" || this.Duration == 0 || this.priorityEvent == "0")){
                    this.message = "You must choose a calendar and a duration"
            }
    else if ((this.selectedDate !== '' && (this.selectedCalendar !== '0' && this.Duration !== 0 && this.priorityEvent !== "0" )) || this.selectedDate === '') {
        const updateToDoPromise = fetch('api/api/todolist/' + this.UpdateToDo.id_todo, {
            method: 'PATCH',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer ' + token
            },
            body: JSON.stringify({ name_todo: this.UpdateToDo.name_todo })
        });

        const updateTasksPromises = this.UpdateToDo.task.map(task => {
            return fetch('api/api/tasks/' + task.id_task, {
                method: 'PATCH',
                headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer ' + token
                },
                body: JSON.stringify({ name_task: task.name_task, description: 'Description', priority_level: task.priority_level, name_todo: this.UpdateToDo.name_todo })
            });
        });
    /*Promise is used to ensure the execution of fetch before*/

    Promise.all([updateToDoPromise, ...updateTasksPromises])
    .then(responses => {
        for (let response of responses) {
        if (!response.ok) {
            throw new Error(response.statusText);

        }
        }
   
        if (this.selectedDate !== '') {
            if (this.selectedCalendar == "0" || this.Duration == 0) {
                this.message = "You must choose a calendar and a duration";
            } else {
                const date = this.selectedDate.split('T')[0].substring(0, 10);
                const time = this.selectedDate.split('T')[1].substring(0, 5);
      
                fetch("api/api/convertToDoToEvent/" + this.UpdateToDo.name_todo, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    },
                    body: JSON.stringify({
                        id_calendar: this.selectedCalendar,
                        description: "Description",
                        start_date: date + ' ' + time,
                        length: this.Duration,
                        priority_level: this.priorityEvent
                    })
                })
                    .then((response) => {
                        if (response.ok) {
                            return response.json();
                        } else {
                            return response.json().then(error => {
                                throw new Error(JSON.stringify(error));
                            });
                        }
                    });
            }
        }

        return Promise.resolve();
        })
        .then(() => {

            this.message = '';
            this.Duration = '0';
            this.selectedDate = "";
            this.selectedCalendar = "0";
            this.Reload();
            })
        .catch(error => {
            let errorMessage;
            try {
                errorMessage = JSON.parse(error.message);
            } catch {
                errorMessage = {
                    message: 'An error occurred while processing your request.'
                };
            }

            this.message = errorMessage.message;
        });
            } else {
                this.message = '';
                this.Duration = '0';
                this.selectedDate = "";
                this.selectedCalendar = "0",
                this.Reload();
            }
    },
  
    OpenTask(index){    
        document.getElementById("myModal" + index).style.display = "block";
        this.selectedCalendar = '0';
        this.selectedDate = '';
    },
    CloseTask(index){
        this.message = '';
        document.getElementById("myModal"+ index).style.display = "none";
    },
    AddToCalendar(){
        if(this.selectedDate == '' || this.selectedCalendar == '0' || this.selectedEvent == '0'){
            this.message = "Please select a Date, Calendar and Event";
        }else{
        const token = localStorage.getItem('token');
        fetch("api/api/attachTaskToEvent/" + this.Task, 
        {
            method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + token
        },
        body: JSON.stringify({id_event : this.selectedEvent})})
        .then((response)=>{    
            if (response.ok) {
            return response.json();
            }
            else { 
                
                return response.json().then(error => {
                    throw new Error(JSON.stringify(error));
            });
        }})
        .catch((error) => {
                    let errorMessage;
                    try {
                        errorMessage = JSON.parse(error.message);
                    } catch {
                        errorMessage = {
                        message: 'An error occurred while processing your request.'
                        };
                    }
                    
                    this.message = errorMessage.message;
                    
                    
                });
        
        this.selectedDate = '';
        this.message = "";
        this.selectedCalendar = '0';
        this.selectedEvent = '0';
        this.Reload();
    }
    },
    OpenList(){
        document.getElementById("NewListModal").style.display = "block";
    },
    CloseList(){
        this.selectedDate = '';
        this.selectedCalendar = '0';
        this.Duration = '';
        this.message = '';
        document.getElementById("NewListModal").style.display = "none";
    }, 
    SubmitList(){
        
        const token = localStorage.getItem('token');
        if(this.ToDo == ''){
                this.message = "You must enter a name for your to do list"
                
        }else if (
        (this.taskInputArray.some((task) => task === '') && !this.selectedImportanceArray.some((priority) => priority === '0')) ||
        (!this.taskInputArray.some((task) => task === '') && this.selectedImportanceArray.some((priority) => priority === '0'))
        ||(!this.taskInput == '' && this.selectedImportance == '0')){
        
            
                this.message = "You must fill all fields for the task";
        }
        else{
           
            if(this.selectedDate !== '' && (this.selectedCalendar == "0" || this.Duration == 0 || this.priorityEvent == "0")){
                    this.message = "You must choose a calendar and a duration"
            }
            else if ((this.selectedDate !== '' && (this.selectedCalendar !== '0' && this.Duration !== 0  && this.priorityEvent !== "0")) || this.selectedDate === '') {
            const List = [];
            if(this.taskInput !== ''){
                if(this.taskChecked != true){ this.taskChecked = false}
                List.push({ name_task : this.taskInput,
                            description : "description",
                            name_todo : this.ToDo,
                            priority_level : this.selectedImportance,
                            is_done : this.taskChecked,
                });
                
            }
            this.AddTasks.forEach((new_task, index) => {
            const checkboxElement = document.getElementById('taskChecked_' + index);
            const inputElement = this.taskInputArray[index];
            const importanceElement = this.selectedImportanceArray[index]

            
            const checkedState = checkboxElement.checked;
            if(inputElement !== ''){
            List.push({ name_task : inputElement,
                        description : "description",
                        priority_level : importanceElement,
                        name_todo : this.ToDo,
                        is_done : checkedState,
            });
            }
        });
        
        const CreateToDoPromise = fetch('api/api/todolist', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            Authorization: 'Bearer ' + token,
        },
        body: JSON.stringify({ name_todo: this.ToDo }),
        });

        let createTaskPromises = [];
        if (List.length !== 0) {
        createTaskPromises = List.map((task) => {
            return fetch('api/api/tasks/fromname', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                Authorization: 'Bearer ' + token,
            },
            body: JSON.stringify({
                name_task: task.name_task,
                description: 'Description',
                priority_level: task.priority_level,
                is_done: task.is_done,
                name_todo: this.ToDo,
            }),
            });
        });
        }


        Promise.all([CreateToDoPromise, ...createTaskPromises])
        .then(responses => {
            for (let response of responses) {
                if (!response.ok) {
                    return response.json().then(error => {
                            throw new Error(JSON.stringify(error));
                    });
                    
                }
            }

        if (this.selectedDate !== '') {
            if (this.selectedCalendar == "0" || this.Duration == 0 || this.priotityEvent == "0") {
                this.message = "You must choose a calendar and a duration";
            } else {
                const date = this.selectedDate.split('T')[0].substring(0, 10);
                const time = this.selectedDate.split('T')[1].substring(0, 5);
                
                fetch("api/api/convertToDoToEvent/" + this.ToDo, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    },
                    body: JSON.stringify({
                        id_calendar: this.selectedCalendar,
                        description: "Description",
                        start_date: date + ' ' + time,
                        length: this.Duration,
                        priority_level: this.priorityEvent
                    })
                })
                    .then((response) => {
                        if (response.ok) {
                            return response.json();
                        } else {
                            return response.json().then(error => {
                                throw new Error(JSON.stringify(error));
                            });
                        }
                    });
            }
        }

        return Promise.resolve();
        })
        .then(() => {
            this.ToDo = '';
            this.message = '';
            this.Duration = '0';
            this.selectedDate = "";
            this.selectedCalendar = "0";
            this.selectedImportanceArray = ["0"];
            this.taskInputArray = [];
            this.Reload();
            })
        .catch(error => {

            let errorMessage;
            try {
                errorMessage = JSON.parse(error.message);
            } catch {
                errorMessage = {
                    message: 'An error occurred while processing your request.'
                };
            }

            this.message = errorMessage.message;
        });
            } else {
                this.ToDo = '';
                this.message = '';
                this.Duration = '0';
                this.selectedDate = "";
                this.selectedCalendar = "0";
                this.selectedImportanceArray = ["0"];
                this.taskInputArray = [];
                this.Reload();
            }
        }
    },
    OpenPlus(task){
        this.Task = task;
        document.getElementById("myModalPlus").style.display = "block";
    },
    ClosePlus(){
        this.selectedDate = '';
        this.message = '';
        document.getElementById("myModalPlus").style.display = "none";
    },
    Reload(){
        window.location.reload();
    }
    },
    beforeMount(){
        
        this.initializePage();
    }
};

window.onload = function () {

    window.onclick = function (event) {
        if (event.target == document.getElementById("myModal") | event.target == document.getElementById("myModalPlus") 
        | event.target == document.getElementById("NewListModal")) {
            window.location.reload();
        }
    };

    // Get the modal
    //var modal = document.getElementById("myModal");
    //var modal = document.getElementById("myModal");
    // Get the button that opens the modal
    //var btn = document.getElementById("addBtn");

    // Get the <span> element that closes the modal
    //var span = document.getElementsByClassName("close")[0];
    // When the user clicks the button, open the modal
    /*if (btn) {
        btn.onclick = function () {
            modal.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span) {
        // When the user clicks on <span> (x), close the modal
        span.onclick = function () {
            modal.style.display = "none";
        };
    } else {
        console.log("element not found");
    }*/
    // When the user clicks anywhere outside of the modal, close it
  
/*
    window.onclick = function (event) {
        if (event.target == document.getElementById("myModalPlus")) {
            document.getElementById("myModalPlus").style.display = "none";
        }
    };

    window.onclick = function (event) {
        if (event.target == document.getElementById("NewListModal")) {
            document.getElementById("NewListModal").style.display = "none";
        }
    };*/
    //dropdown list
    //var x, i, j, l, ll, selElmnt, a, b, c;
    /*look for any elements with the class "custom-select":*/
 /*   x = document.getElementsByClassName("custom-select");
    l = x.length;
    for (i = 0; i < l; i++) {
        selElmnt = x[i].getElementsByTagName("select")[0];
        ll = selElmnt.length;
        /*for each element, create a new DIV that will act as the selected item:*/
 /*       a = document.createElement("DIV");
        a.setAttribute("class", "select-selected");
        a.innerHTML = selElmnt.options[selElmnt.selectedIndex].innerHTML;
        x[i].appendChild(a);
        /*for each element, create a new DIV that will contain the option list:*/
  /*      b = document.createElement("DIV");
        b.setAttribute("class", "select-items select-hide");
        for (j = 1; j < ll; j++) {
            /*for each option in the original select element,
                  create a new DIV that will act as an option item:*/
   /*         c = document.createElement("DIV");
            c.innerHTML = selElmnt.options[j].innerHTML;
            c.addEventListener("click", function () {
                /*when an item is clicked, update the original select box,
                        and the selected item:*/
  /*              var y, i, k, s, h, sl, yl;
                s = this.parentNode.parentNode.getElementsByTagName("select")[0];
                sl = s.length;
                h = this.parentNode.previousSibling;
                for (i = 0; i < sl; i++) {
                    if (s.options[i].innerHTML == this.innerHTML) {
                        s.selectedIndex = i;
                        h.innerHTML = this.innerHTML;
                        y = this.parentNode.getElementsByClassName("same-as-selected");
                        yl = y.length;
                        for (k = 0; k < yl; k++) {
                            y[k].removeAttribute("class");
                        }
                        this.setAttribute("class", "same-as-selected");
                        break;
                    }
                }
                h.click();
            });
            b.appendChild(c);
        }
        x[i].appendChild(b);
        a.addEventListener("click", function (e) {
            /*when the select box is clicked, close any other select boxes,
                  and open/close the current select box:*/
   /*         e.stopPropagation();
            closeAllSelect(this);
            this.nextSibling.classList.toggle("select-hide");
            this.classList.toggle("select-arrow-active");
        });
    }

    function closeAllSelect(elmnt) {
        /*a function that will close all select boxes in the document,
            except the current select box:*/
   /*     var x,
            y,
            i,
            xl,
            yl,
            arrNo = [];
        x = document.getElementsByClassName("select-items");
        y = document.getElementsByClassName("select-selected");
        xl = x.length;
        yl = y.length;
        for (i = 0; i < yl; i++) {
            if (elmnt == y[i]) {
                arrNo.push(i);
            } else {
                y[i].classList.remove("select-arrow-active");
            }
        }
        for (i = 0; i < xl; i++) {
            if (arrNo.indexOf(i)) {
                x[i].classList.add("select-hide");
            }
        }
    }*/
    
/*
    // Get the modal2
    var modal1 = document.getElementById("myModalPlus");

    // Get the button that opens the modal
    var btn1 = document.getElementById("TaskPlus");

    // Get the <span> element that closes the modal
    var span1 = document.getElementsByClassName("close")[1];

    // When the user clicks the button, open the modal
    if (btn1) {
        btn1.onclick = function () {
            modal1.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span1) {
        // When the user clicks on <span> (x), close the modal
        span1.onclick = function () {
            modal1.style.display = "none";
        };
    } else {
        console.log("element not found");
    }

    */
    // When the user clicks anywhere outside of the modal, close it
  
/*
    // Get the modal2
    var modal2 = document.getElementById("NewListModal");

    // Get the button that opens the modal
    var btn2 = document.getElementById("AddList");

    // Get the <span> element that closes the modal
    var span2 = document.getElementsByClassName("close")[2];

    // When the user clicks the button, open the modal
    if (btn2) {
        btn2.onclick = function () {
            modal2.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span2) {
        // When the user clicks on <span> (x), close the modal
        span2.onclick = function () {
            modal2.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
*/
    // When the user clicks anywhere outside of the modal, close it
   
};
</script>

<style></style>
