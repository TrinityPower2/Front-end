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
                    <router-link to="/calendar-page" class="to-page-nav">My Plannings</router-link>
                    <router-link to="/todo-list2-page" class="to-page-nav">My Todo Lists</router-link>
                    <router-link to="/create-calendar-page" class="to-page-nav">Create a Planning</router-link>
                </div>
                <UserMenu></UserMenu>
                <div class="light">
                    <DarkLightMode></DarkLightMode>
                </div>
            </div>
        </header>
        <a id="top"></a>
        <div class="create-calendar-container">
            <div class="create-container">
                <div class="FormBox">
                    <div class="FormContainer">
                        <div class="Form-banner-container">
                            <div class="loginForm">
                                <h2>Create Calendar</h2>
                                <p class="Form-presentation"> <br> TimeToDo depends on an <i class="fa fa-bold"
                                        aria-hidden="true">algorithm</i> to optimize your plannings. <br><br> Please enter
                                    the tasks you need to complete this week ! <br><br></p>
                                <div class="created-tasks-container">
                                    <div class="created-tasks-new" style="--color:#F291BB;">
                                        <p class="created-tasks-title">
                                            Soirée d'anniv hihi
                                        </p>
                                        <p class="created-tasks-title">
                                            5H
                                        </p>
                                        <span class="close" @click="OpenmyModalEventDelete">&times;</span>
                                    </div>
                                    <div class="created-tasks-new" style="--color:#90B5FF;">
                                        <p class="created-tasks-title">
                                            Projet d'IA
                                        </p>
                                        <p class="created-tasks-title">
                                            18H
                                        </p>
                                        <span class="close" @click="OpenmyModalEventDelete">&times;</span>
                                    </div>
                                </div>
                                <button class="Create-planning-Btn" id="addCalendar" @click="OpenmyModaladdNewCalendar">
                                    Generate Planning
                                </button>
                                <!-- <div >
                                    <input type="submit" value="" name="btnUpdate" />
                                </div> -->
                                <p class="forgotPswd MoveOn">
                                    Not done yet ?<btn id="AddNewTask">Add Task</btn>
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="create-calendar-event" id="create-calendar-event">
                <div class="modal-content-create">
                    <span class="close">&times;</span>
                    <h1 class="modal-Title" style="margin-bottom : 40px;">New Event</h1>
                    <div class="modal-center1">

                        <input type="text" id="fname" name="fname" class="new-task-input" placeholder="Event Name"><br>
                        <div class="New-list-element1" style="margin-top : 40px;">
                            <!-- <div class="new-list-desc">
                                    Day
                                </div> -->
                            <font-awesome-icon icon="fa-regular fa-clock" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Length of event :</option>
                                    <option value="1">1H</option>
                                    <option value="2">2H</option>
                                    <option value="3">3H</option>
                                    <option value="4">4H</option>
                                    <option value="5">5H</option>
                                    <option value="6">6H</option>
                                    <option value="7">7H</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-regular fa-calendar-days" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Choose day :</option>
                                    <option value="1">Monday</option>
                                    <option value="2">Tuesday</option>
                                    <option value="3">Wednesday</option>
                                    <option value="4">Thursday</option>
                                    <option value="5">Friday</option>
                                    <option value="6">Saturday</option>
                                    <option value="7">Sunday</option>
                                    <option value="8">No Preference</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <!-- <div class="new-list-desc">
                                    Add
                                </div> -->
                            <font-awesome-icon icon="fa-regular fa-hourglass-half" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="Timeslots-choice">
                                <div class="custom-select create-select" id="Time-Task">
                                    <select>
                                        <option value="0">Start</option>
                                        <option value="1">1H00</option>
                                        <option value="2">2H00</option>
                                        <option value="3">3H00</option>
                                        <option value="4">4H00</option>
                                        <option value="5">5H00</option>
                                    </select>
                                </div>
                                <div class="custom-select create-select" id="Time-Task">
                                    <select>
                                        <option value="0">End</option>
                                        <option value="1">1H00</option>
                                        <option value="2">2H00</option>
                                        <option value="3">3H00</option>
                                        <option value="4">4H00</option>
                                        <option value="5">5H00</option>
                                    </select>
                                </div>
                            </div>
                        </div>

                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-palette" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Type of event :</option>
                                    <option value="1"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #00ff88;" /> Party</option>
                                    <option value="2"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #0084ff;" /> Project</option>
                                    <option value="3"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #d400ff;" /> Work</option>
                                    <option value="4"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff00ae;" /> Health</option>
                                    <option value="5"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff0033;" /> Holiday</option>
                                    <option value="6"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff8800;" /> Family</option>
                                    <option value="7"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffdd00;" /> Class</option>
                                    <option value="8"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffffff;" /> Custom</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-repeat" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Frequence :</option>
                                    <option value="1">Every day</option>
                                    <option value="2">Every 2 days</option>
                                    <option value="3">Every 3 days</option>
                                    <option value="4">Weekly</option>
                                    <option value="5">Twice a day</option>
                                    <option value="6">None</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-regular fa-bell" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Notifications :</option>
                                    <option value="1">At event time</option>
                                    <option value="2">1H before</option>
                                    <option value="3">1 day before</option>
                                    <option value="4">2 days before</option>
                                    <option value="5">Never</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-circle-exclamation" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Importance :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element" style="margin-left:14%">
                            <font-awesome-icon icon="fa-solid fa-list-check" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <!-- <div class="custom-select create-select">
                                <select>
                                    <option value="0">ToDo List :</option>
                                </select>
                            </div> -->

                        </div>
                        <div class="Add-another-container">
                            <div class="Add-another-task">
                                <div class="new-task-create">
                                    <label class="task-container" style="margin-left: 0%;">
                                        <input type="checkbox" />
                                        <span class="checkmark"></span>
                                    </label>
                                    <input type="text" id="fname" name="fname" class="new-task-input" placeholder="My Task">
                                    <font-awesome-icon icon="fa-solid fa-plus" size="sm"
                                        style="transform:rotate(45deg); margin-left: 13px;" /><br>
                                </div>
                                <div class="new-task-create">
                                    <font-awesome-icon icon="fa-solid fa-plus" size="sm" />
                                    <p>Add Task</p>
                                </div>
                            </div>
                        </div>
                        <div style="width:90%; display:flex; justify-content:center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            



            <div id="NewCalendarModal" class="modal1">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close">&times;</span>
                    <h1 class="modal-Title" style="margin-bottom : 40px;">Generate Planning</h1>
                    <div class="modal-center2">
                        <div class="New-list-element">
                            <div class="new-list-desc">
                                Lunch Duration
                            </div>
                            <div class="custom-select" id="Time-Task">
                                <select>
                                    <option value="0">Start</option>
                                    <option value="1">1H00</option>
                                    <option value="2">2H00</option>
                                    <option value="3">3H00</option>
                                    <option value="4">4H00</option>
                                    <option value="5">5H00</option>
                                </select>
                            </div>
                            <p class="hyphen">-</p>
                            <div class="custom-select" id="Time-Task">
                                <select>
                                    <option value="0">End</option>
                                    <option value="1">1H00</option>
                                    <option value="2">2H00</option>
                                    <option value="3">3H00</option>
                                    <option value="4">4H00</option>
                                    <option value="5">5H00</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element">
                            <div class="new-list-desc">
                                Superpose
                            </div>
                            <div class="custom-select">
                                <select>
                                    <option value="0">Select planning :</option>
                                    <option value="1">Monday</option>
                                    <option value="2">Tuesday</option>
                                    <option value="3">Wednesday</option>
                                    <option value="4">Thursday</option>
                                    <option value="5">Friday</option>
                                    <option value="6">Saturday</option>
                                    <option value="7">Sunday</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element">
                            <div class="new-list-desc">
                                Colors
                            </div>
                            <div class="custom-select">
                                <select>
                                    <option value="0">Choose a Color :</option>
                                    <option value="1"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #00ff88;" /> Green</option>
                                    <option value="2"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #0084ff;" /> Blue</option>
                                    <option value="3"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #d400ff;" /> Purple</option>
                                    <option value="4"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff00ae;" /> Pink</option>
                                    <option value="5"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff0033;" /> Red</option>
                                    <option value="6"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff8800;" /> Orange</option>
                                    <option value="7"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffdd00;" /> Yellow</option>
                                    <option value="8"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffffff;" /> Custom</option>
                                </select>
                            </div>
                        </div>

                        <div style="width:65%; display:flex; justify-content:center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="myModaladdNewCalendar" class="modal">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close" @click="ClosemyModaladdNewCalendar">&times;</span>
                    <h1 class="modal-Title">Add a new Calendar</h1>
                    <div class="modal-center">
                        <p style="margin-top: 50px;">Would you like to create a new calendar or add it to an existing one ?
                        </p>
                        <div class="delete-list-button">
                            <div class="AddTaskInputBox no">
                                <input class="close" type="submit" @click="OpenmyModalPlus" value="Add to Calendar" name="submit"
                                    id="add-to-pop-up" />
                            </div>
                            <div class="AddTaskInputBox no">
                                <input @click="OpenCreateCalendarModal" style="margin-left: 0px;" type="submit" value="New Blank Calendar" name="submit"
                                    id="blankCalendar" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="myModalPlus" class="modal">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close" @click="ClosemyModalPlus">&times;</span>
                    <h1 class="modal-Title">Add to Calendar</h1>
                    <div class="modal-center">
                        <div class="custom-select">
                            <select>
                                <option value="0">Choose Calendar
                                </option>
                                <option value="1">Calendar1</option>
                                <option value="2">Calendar2</option>
                                <option value="3">Calendar3</option>
                                <option value="4">Calendar4</option>
                                <option value="5">Calendar5</option>
                            </select>
                        </div>
                        <div class="AddInputBox">
                            <input type="submit" value="Add" name="submit" />
                        </div>
                    </div>
                </div>
            </div>

            <div id="ImportCalendarModal" class="modal1">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close" @click="CloseImportCalendarModal">&times;</span>
                    <h1 class="modal-Title" style="margin-bottom : 40px;">Import Planning</h1>
                    <div class="modal-center2">
                        <div class="New-list-element">
                            <label class="new-list-desc" for="fileInput">Select File</label>
                            <input type="file"  id="fileInput" accept=".ics" @change="handleFileChange" style="display: none;">
                            <div class="Create-planning-Btn" @click="openFileInput" style="margin-left: 33px;">{{ labelText }}</div>
                        </div>
                        <div class="New-list-element">
                            <div class="new-list-desc">
                                Name of Calendar
                            </div>
                            <input v-model="CalendarName" type="text" id="fname" name="fname" class="new-task-input"
                                placeholder="Calendar Name" /><br />
                        </div>
                        <div class="New-list-element">
                            <div class="new-list-desc">
                                Colors
                            </div>
                            <div class="custom-select">
                                <select class="select-items" v-model="CalColor">
                                    <option value="0">Choose a Color :</option>
                                    <option value="green"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #00ff88;" />
                                        Green</option>
                                    <option value="blue"><font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff;" />
                                        Blue</option>
                                    <option value="purple"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #d400ff;" />
                                        Purple</option>
                                    <option value="pink"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae;" />
                                        Pink</option>
                                    <option value="red"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033;" />
                                        Red</option>
                                    <option value="orange"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff8800;" />
                                        Orange</option>
                                    <option value="yellow"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffdd00;" />
                                        Yellow</option>
                                    <option value="white"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffffff;" />
                                        White</option>
                                </select>
                            </div>
                        </div>
                        <br><br>
                        <div class="message"> {{ message }}</div><br>
                        <div style="width:50%; display:flex; justify-content:center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input @click="UploadFile" type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="CreateCalendarModal" class="modal1">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close" @click="CloseCreateCalendarModal">&times;</span>
                <h1 class="modal-Title" style="margin-bottom : 40px;">Create Planning</h1>
                <div class="modal-center2">
                    <div class="New-list-element">
                        <div class="new-list-desc">
                            Name of Calendar
                        </div>
                        <input v-model="CalendarName" type="text" id="fname" name="fname" class="new-task-input"
                            placeholder="Calendar Name" /><br />
                    </div>
                    <div class="New-list-element">
                        <div class="new-list-desc">
                            Colors
                        </div>
                        <div class="custom-select">
                            <select class="select-items" v-model="CalColor">
                                <option value="0">Choose a Color :</option>
                                <option value="green"><font-awesome-icon icon="fa-solid fa-circle"
                                        style="color: #00ff88;" />
                                    Green</option>
                                <option value="blue"><font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff;" />
                                    Blue</option>
                                <option value="purple"><font-awesome-icon icon="fa-solid fa-circle"
                                        style="color: #d400ff;" />
                                    Purple</option>
                                <option value="pink"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae;" />
                                    Pink</option>
                                <option value="red"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033;" />
                                    Red</option>
                                <option value="orange"><font-awesome-icon icon="fa-solid fa-circle"
                                        style="color: #ff8800;" />
                                    Orange</option>
                                <option value="yellow"><font-awesome-icon icon="fa-solid fa-circle"
                                        style="color: #ffdd00;" />
                                    Yellow</option>
                                <option value="white"><font-awesome-icon icon="fa-solid fa-circle"
                                        style="color: #ffffff;" />
                                    White</option>
                            </select>
                        </div>
                    </div>
                    <br><br>
                    <div class="message"> {{ message }}</div><br>
                    <div style="width:50%; display:flex; justify-content:center; margin-top: 50px;">
                        <div class="AddTaskInputBox">
                            <input @click="CreateCalendar" type="submit" value="Add" name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="myModalEventDelete" class="modal">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close" @click="ClosemyModalEventDelete">&times;</span>
                <h1 class="modal-Title">Delete Event</h1>
                <div class="modal-center">
                    <p style="margin-top: 50px;">Are you sure you want to delete this Event ?</p>
                    <div class="delete-list-button">
                        <div class="AddTaskInputBox no">
                            <input @click="cancelDeleteTask" class="close" type="submit" value="Cancel" name="submit" />
                        </div>
                        <div class="AddTaskInputBox no">
                            <input @click="deleteTask" style="margin-left: 0px;" type="submit" value="Delete" name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <div class="create-calendar-event" id="create-calendar-event" style="display:block">
            <div class="modal-content-create">
                <span class="close">&times;</span>
                <h1 class="modal-Title" style="margin-bottom : 40px;">Your new Calendar</h1>
                <div class="modal-center3">

                    <!-- <input type="text" id="fname" name="fname" class="new-task-input" placeholder="Event Name"><br> -->
                    <div class="New-list-element1" style="width: 28%;">
                        <div class="FormBox">
                            <div class="FormContainer">
                                <div class="Form-banner-container">
                                    <div class="loginForm">
                                        <h2>Dropped Tasks</h2>
                                        <p class="Form-presentation"> <br> The following tasks <i class="fa fa-bold"
                                                aria-hidden="true">couldn't be fit</i> in the newly generated
                                            algorithm.<br><br> If this is okay with you please <i class="fa fa-bold"
                                                aria-hidden="true">validate</i> below.<br><br> Otherwise, please check if
                                            you've entered too many tasks, or concurring tasks and choose to <i
                                                class="fa fa-bold" aria-hidden="true">reselect</i> below. <br><br></p>
                                        <div class="created-tasks-container">
                                            <div class="created-tasks-new-container">
                                                <div class="created-tasks-new" style="--color:#F291BB;">
                                                    <p class="created-tasks-title">
                                                        Soirée d'anniv hihi
                                                    </p>

                                                    <p class="created-tasks-title">
                                                        5H
                                                    </p>
                                                </div>
                                                <!-- <font-awesome-icon icon="fa-solid fa-plus" size="sm" class="new-task-remove" style="transform:rotate(45deg); margin-left: 13px;" /> -->
                                            </div>
                                            <div class="created-tasks-new-container">
                                                <div class="created-tasks-new" style="--color:#90B5FF;">
                                                    <p class="created-tasks-title">
                                                        Projet d'IA
                                                    </p>
                                                    <p class="created-tasks-title">
                                                        18H
                                                    </p>
                                                </div>
                                                <!-- <font-awesome-icon icon="fa-solid fa-plus" size="sm" class="new-task-remove" style="transform:rotate(45deg); margin-left: 13px;" /> -->
                                            </div>
                                        </div>
                                        <!--<button class="Create-planning-Btn" id="addCalendar">
                                            Generate Planning
                                        </button>
                                         <div >
                                    <input type="submit" value="" name="btnUpdate" />
                                </div> 
                                        <p class="forgotPswd MoveOn">
                                            Not done yet ?<btn id="AddNewTask">Add Event</btn>
                                        </p>-->
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="New-list-element1" style="margin-top : 40px;">
                        <div class="calendar-container">
                            <div class="calendar">
                                <div class="timeline">

                                    <div class="time-marker">6 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">6H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">7 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">7H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">8 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">8H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">9 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">9H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">10 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">10H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">11 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">11H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">12 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">12H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">13 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">13H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">14 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">14H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">15 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">15H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">16 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">16H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">17 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">17H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">18 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">18H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">19 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">19H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">20 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">20H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">21 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">21H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">22 H</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker mid">22H30</div>
                                    <div class="time-marker"></div>
                                    <div class="time-marker">23 H</div>

                                </div>
                                <div class="days">
                                    <div class="day mon">
                                        <div class="date">
                                            <p class="date-num">9</p>
                                            <p class="date-day">Mon</p>
                                        </div>
                                        <div class="events">
                                            <div class="event start-13 end-15 project calendar-8">
                                                <p class="calendar-title">Physics exam</p>
                                                <p class="calendar-time">13H - 15H</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="day tues">
                                        <div class="date">
                                            <p class="date-num">10</p>
                                            <p class="date-day">Tues</p>
                                        </div>
                                        <div class="events">
                                            <div class="event start-16 end-18-30 health calendar-8" id="event">
                                                <p class="calendar-title">Volleyball Practice</p>
                                                <p class="calendar-time">16H - 18H30</p>
                                            </div>
                                            <div class="event start-10 end-11-30 class calendar-8">
                                                <p class="calendar-title">Meeting</p>
                                                <p class="calendar-time">10H - 11H30</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="day wed">
                                        <div class="date">
                                            <p class="date-num">11</p>
                                            <p class="date-day">Wed</p>
                                        </div>
                                        <div class="events">
                                            <div class="event start-12 end-19 holiday calendar-8">
                                                <p class="calendar-title">Dentist Apointment</p>
                                                <p class="calendar-time">12H - 19H</p>
                                            </div>
                                            <div class="event start-8 end-9-30 project calendar-8">
                                                <p class="calendar-title">Maths Exam</p>
                                                <p class="calendar-time">8H - 9H30</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="day thurs">
                                        <div class="date">
                                            <p class="date-num">12</p>
                                            <p class="date-day">Thurs</p>
                                        </div>
                                        <div class="events">
                                            <div class="event start-10 end-12 health calendar-8">
                                                <p class="calendar-title">Volleyball Practice</p>
                                                <p class="calendar-time">10H - 12H</p>
                                            </div>
                                            <div class="event start-19 end-23 party calendar-8">
                                                <p class="calendar-title">Entertainment</p>
                                                <p class="calendar-time">19H - 23H</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="day fri">
                                        <div class="date">
                                            <p class="date-num">13</p>
                                            <p class="date-day">Fri</p>
                                        </div>
                                        <div class="events">
                                        </div>
                                    </div>
                                    <div class="day sat">
                                        <div class="date">
                                            <p class="date-num">14</p>
                                            <p class="date-day">Sat</p>
                                        </div>
                                        <div class="events">
                                            <div class="event start-11 end-16 work calendar-8">
                                                <p class="calendar-title">Volleyball Practice</p>
                                                <p class="calendar-time">11H - 16H</p>
                                            </div>
                                            <div class="event start-17 end-20 family calendar-8">
                                                <p class="calendar-title">Family Gathering</p>
                                                <p class="calendar-time">15H - 20H</p>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="day sun">
                                        <div class="date">
                                            <p class="date-num">15</p>
                                            <p class="date-day">Sun</p>
                                        </div>
                                        <div class="events">
                                            <div class="event start-11 end-15 holiday calendar-8">
                                                <p class="calendar-title">Flight to Dubai</p>
                                                <p class="calendar-time">11H - 15H</p>
                                            </div>
                                            <div class="event start-7 end-9 project calendar-8">
                                                <p class="calendar-title">English Exam</p>
                                                <p class="calendar-time">7H - 9H</p>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="delete-list-button">
                        <div class="AddTaskInputBox no">
                            <input class="close" type="submit" value="Generate Planning !" name="submit" />
                        </div>
                        <div class="AddTaskInputBox no">
                            <input style="margin-left: 0px;" type="submit" value="Go Back To Review ->" name="submit" />
                        </div>
                    </div>
            </div>
        </div>


        <div class="import-button-container">
            <button class="Create-planning-Btn" @click="OpenImportCalendarModal" id="importCalendar">
                Import Planning
            </button>
        </div>
        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"><font-awesome-icon
                icon="fa-solid fa-arrow-up" size="xs" style="color: #fff0fe;" /></a>
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
import UserMenu from "../components/UserMenu.vue";
import DarkLightMode from "../components/DarkLightMode.vue";
export default {
    name: "CreateCalendarPage",
    components: {
        DarkLightMode,
        UserMenu
    },
    data() {
        return {
            SelectedCalendar: "0",
            SelectedImportance: "0",
            Calendar: [],
            selectedWeek: "",
            EventByWeek: [],
            days: ['mon', 'tues', 'wed', 'thurs', 'fri', 'sat', 'sun'],
            daysOfWeek: [],
            SelectedFrequence: "first",
            SelectedIndex: "",
            SelectedType: "0",
            SelectedDay: "0",
            SelectedEventName: "",
            SelectedLength: "0",
            StartTime: "0",
            EndTime: "0",
            SelectedEvent: "",
            labelText: 'No file selected',
            selectedFile: null,
            CalColor: "0",
            SelectedDate: "",
            CalendarName: "",
            AddTasks: [],
            visibleCalendars: [],
            message: "",
            notificationEnabled: false
        }
    },
    methods: {
        async Fill() {

            const cal = await this.Calendar.find(calendar => calendar.id_calendar === this.SelectedCalendar);
            this.CalendarName = cal.name_calendar;
            this.CalColor = cal.calendar_color;
            this.notificationEnabled = cal.to_notify;
            console.log(cal.name_calendar);
            console.log(cal.calendar_color);
        },

        OpenCreateCalendarModal() {
            document.getElementById("CreateCalendarModal").style.display = "block";
        },
        CloseCreateCalendarModal() {
            document.getElementById("CreateCalendarModal").style.display = "none";
            this.message = "";
        },
        CreateCalendar() {
            if (this.CalendarName == '' || this.CalColor == "0") {
                this.message = 'You must fill all the required fields'
            } else {

                const token = localStorage.getItem('token');
                fetch("api/api/calendar",
                    {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                            'Authorization': 'Bearer ' + token
                        },
                        body: JSON.stringify({ name_calendar: this.CalendarName, color: this.CalColor })
                    })
                    .then((response) => {
                        console.log(response.json())
                        if (response.ok) {
                            this.message = '';
                            this.Reload();
                            return response.json();

                        }
                        else {

                            return response.json().then(error => {
                                throw new Error(JSON.stringify(error));
                            });
                        }
                    })
                    .catch((error) => {
                        let errorMessage;
                        try {
                            errorMessage = JSON.parse(error.message);
                        } catch {
                            errorMessage = {
                                message: ' '
                            };
                        }

                        this.message = errorMessage.message;


                    });
                this.message = '';
                this.CalColor = "0";
                this.CalendarName = "";

            }
        },
        OpenmyModaladdNewCalendar() {
            document.getElementById("myModaladdNewCalendar").style.display = "block";
        },
        ClosemyModaladdNewCalendar() {
            document.getElementById("myModaladdNewCalendar").style.display = "none";
            this.message = "";
            this.SelectedType = "0";
            this.SelectedFrequence = "first";
            this.SelectedEventName = " "
            this.SelectedDay = "0";
            this.StartTime = "0"
            this.SelectedDate = "0"
            this.EndTime = "0"
            this.message = ""
        },
        OpenmyModalPlus() {
            document.getElementById("myModalPlus").style.display = "block";
        },
        ClosemyModalPlus() {
            document.getElementById("myModalPlus").style.display = "none";
            this.message = "";
            this.SelectedType = "0";
            this.SelectedFrequence = "first";
            this.SelectedEventName = " "
            this.SelectedDay = "0";
            this.StartTime = "0"
            this.SelectedDate = "0"
            this.EndTime = "0"
            this.message = ""
        },
        OpenImportCalendarModal() {
            document.getElementById("ImportCalendarModal").style.display = "block";
        },
        CloseImportCalendarModal() {
            document.getElementById("ImportCalendarModal").style.display = "none";
            this.message = "";
        },
        OpenmyModalEventDelete() {
            document.getElementById("myModalEventDelete").style.display = "block";
        },
        ClosemyModalEventDelete() {
            document.getElementById("myModalEventDelete").style.display = "none";
            this.message = "";
        },
        deleteTask() {
        var element = document.querySelector('.created-tasks-new');
        element.remove();
        document.getElementById("myModalEventDelete").style.display = "none";
        },
        cancelDeleteTask() {
            document.getElementById("myModalEventDelete").style.display = "none";
        },
    },
    mounted() {
        var thisID = document.getElementById("TopBtn");
        var myScrollFunc = function () {
            var y = window.scrollY;
            if (y >= 300) {
                thisID.className = "fa fa-angle-double-up show";
            } else {
                thisID.className = "fa fa-angle-double-up hide";
            }
        };
        window.addEventListener("scroll", myScrollFunc);
        window.addEventListener("beforeunload", this.handleBeforeUnload);
        const week = localStorage.getItem("selectedWeek");
        this.selectedWeek = week;
        this.getDaysOfWeek();
    },
};
/*
window.onload = function () {
    // Get the modal
    var modal = document.getElementById("create-calendar-event");

    // Get the button that opens the modal
    var btn = document.getElementById("AddNewTask");

    // Get the <span> element that closes the modal
    var span = document.getElementsByClassName("close")[0];

    // When the user clicks the button, open the modal
    if (btn) {
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
    }
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal) {
            modal.style.display = "none";
        }
    };



    // Get the modal2
    var modal1 = document.getElementById("myModalPlus");

    // Get the button that opens the modal
    var btn1 = document.getElementById("add-to-pop-up");

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
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal1) {
            modal1.style.display = "none";
        }
    };


    // Get the modal2
    var modal2 = document.getElementById("myModaladdNewCalendar");

    // Get the button that opens the modal
    var btn2 = document.getElementById("addCalendar");

    // Get the <span> element that closes the modal
    var span2 = document.getElementsByClassName("close")[1];

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
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal2) {
            modal2.style.display = "none";
        }
    };

    // Get the modal3
    var modal3 = document.getElementById("ImportCalendarModal");

    // Get the button that opens the modal
    var btn3 = document.getElementById("importCalendar");

    // Get the <span> element that closes the modal
    var span3 = document.getElementsByClassName("close")[2];

    // When the user clicks the button, open the modal
    if (btn3) {
        btn3.onclick = function () {
            modal3.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span3) {
        // When the user clicks on <span> (x), close the modal
        span3.onclick = function () {
            modal3.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal3) {
            modal3.style.display = "none";
        }
    };



    // Get the modal2
    var modal4 = document.getElementById("myEventDelete");

    // Get the button that opens the modal
    var btn4 = document.getElementsByClassName("new-task-remove");

    // Get the <span> element that closes the modal
    var span4 = document.getElementsByClassName("close")[3];

    // When the user clicks the button, open the modal
    if (btn4) {
        btn4.onclick = function () {
            modal4.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span4) {
        // When the user clicks on <span> (x), close the modal
        span4.onclick = function () {
            modal4.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal4) {
            modal4.style.display = "none";
        }
    };


    //dropdown list

    var x, i, j, l, ll, selElmnt, a, b, c;
    /*look for any elements with the class "custom-select":
    x = document.getElementsByClassName("custom-select");
    l = x.length;
    for (i = 0; i < l; i++) {
        selElmnt = x[i].getElementsByTagName("select")[0];
        ll = selElmnt.length;
        /*for each element, create a new DIV that will act as the selected item:
        a = document.createElement("DIV");
        a.setAttribute("class", "select-selected");
        a.innerHTML = selElmnt.options[selElmnt.selectedIndex].innerHTML;
        x[i].appendChild(a);
        /*for each element, create a new DIV that will contain the option list:
        b = document.createElement("DIV");
        b.setAttribute("class", "select-items select-hide");
        for (j = 1; j < ll; j++) {
            /*for each option in the original select element,
                  create a new DIV that will act as an option item:
            c = document.createElement("DIV");
            c.innerHTML = selElmnt.options[j].innerHTML;
            c.addEventListener("click", function () {
                /*when an item is clicked, update the original select box,
                        and the selected item:
                var y, i, k, s, h, sl, yl;
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
                  and open/close the current select box:
            e.stopPropagation();
            closeAllSelect(this);
            this.nextSibling.classList.toggle("select-hide");
            this.classList.toggle("select-arrow-active");
        });
    }
    function closeAllSelect(elmnt) {
        /*a function that will close all select boxes in the document,
            except the current select box:
        var x,
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
    }
    /*if the user clicks anywhere outside the select box,
      then close all select boxes:
    document.addEventListener("click", closeAllSelect);



};
*/
</script>

<style></style>
