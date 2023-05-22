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

                                <div class="created-tasks-container1" v-for="(event, index) in Tasks.events" :key="index">
                                    <div :class='"created-tasks-new1 " + event.color'>
                                        <p class="created-tasks-title">
                                            {{ event.name }}
                                        </p>
                                        <p class="created-tasks-title">
                                            {{ event.duration }}H
                                        </p>
                                        <span style="color:#6b666b50; " class="close"
                                            @click="OpenmyModalEventDelete(index)">&times;</span>
                                    </div>
                                </div>

                                <button class="Create-planning-Btn" id="addCalendar" @click="OpenmyModaladdNewCalendar">
                                    Generate Planning
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="create-calendar-event" id="create-calendar-event">
                <div class="modal-content-create">
                    <span class="close">&times;</span>
                    <h1 class="modal-Title" style="margin-bottom : 40px;">New Event</h1>
                    <br>
                    <div v-if="showAlert && invalidField === 'SelectedDate'" class="message">Time
                        must be between 06:00 and 23:00</div>
                    <br>
                    <div class="modal-center">
                        <input v-model="SelectedEventName" type="text" id="fname" name="fname" class="new-task-input"
                            placeholder="Event Name"><br>
                    </div>
                    <div class="modal-center2">


                        <div class="New-list-element1" style="margin-top : 40px;">
                            <font-awesome-icon icon="fa-regular fa-clock" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />

                            <div class="custom-select2">
                                <select class="select-items" style="position:static;" v-model="SelectedDuration">
                                    <option value="0">Length of event :</option>
                                    <option value="1">1H</option>
                                    <option value="2">2H</option>
                                    <option value="3">3H</option>
                                    <option value="4">4H</option>
                                    <option value="5">5H</option>
                                    <option value="6">6H</option>
                                    <option value="7">7H</option>
                                    <option value="8">8H</option>
                                    <option value="9">9H</option>
                                    <option value="10">10H</option>
                                    <option value="11">11H</option>
                                    <option value="12">12H</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-regular fa-calendar-days" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />


                            <div class="custom-select2" id="Time-Task">
                                <input v-model="SelectedDate" class="DescriptionInput2" type="datetime-local" id="day"
                                @blur="ValidateTime('SelectedDate')" name="day-task" min="2023-05-22T06:00" max="2028-12-30T23:00">
                            </div>

                        </div>

                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-palette" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select class="select-items" style="position:static;" v-model="SelectedType">
                                    <option value="0">Type of event :</option>
                                    <option value="red"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #00ff88" />Party</option>
                                    <option value="yellow"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #0084ff" />Project</option>
                                    <option value="blue"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #d400ff" />Work</option>
                                    <option value="green"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff00ae" />Health</option>
                                    <option value="purple"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff0033" />Holiday</option>
                                    <option value="pink"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff8800" />Family</option>
                                    <option value="orange"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffdd00" />Class</option>
                                    <option value="white"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ffffff" />Friends</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-repeat" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select class="select-items" style="position:static;" v-model="SelectedFrequence">
                                    <option value="first">Choose Frequence : </option>
                                    <option value="6">Every day</option>
                                    <option value="5">Every 2 days</option>
                                    <option value="4">Every 3 days</option>
                                    <option value="3">Weekly</option>
                                    <option value="2">Monthly</option>
                                    <option value="1">Yearly</option>
                                    <option value="0">None</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-circle-exclamation" size="xl"
                                style="color: rgba(85, 84, 85, 0.986);" />
                            <div class="custom-select create-select">
                                <select class="select-items" style="position:static;" v-model="SelectedImportance">
                                    <option value="0">Importance :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                            </div>
                        </div>
                        <div style="margin-left:132px;">
                            <div class="message1"> {{ message }}</div><br>
                        </div>
                        <div style="width: 90%; display: flex; justify-content: center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input @click="AddEvent" type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="myModaladdNewCalendar" class="modal1">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close" @click="ClosemyModaladdNewCalendar">&times;</span>
                    <h1 class="modal-Title">Add a new Calendar</h1>
                    <div class="modal-center">
                        <p style="margin-top: 50px;">Would you like to create a new calendar or add it to an existing
                            one ?
                        </p>
                        <div class="delete-list-button">
                            <div class="AddTaskInputBox no">
                                <input class="close" type="submit" @click="AddToCalendarFromAddANewCalendar"
                                    value="Add to Calendar" name="submit" id="add-to-pop-up" />
                            </div>
                            <div class="AddTaskInputBox no">
                                <input @click="NewBlankCalendarFromAddANewCalendar" style="margin-left: 0px;" type="submit"
                                    value="New Blank Calendar" name="submit" id="blankCalendar" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="myModalPlus" class="modal1">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close" @click="ClosemyModalPlus">&times;</span>
                    <h1 class="modal-Title">Add to Calendar</h1>
                    <div class="modal-center">
                        <div class="custom-select2" style="margin-top:43px;">
                            <select class="select-items" v-model="SelectedCalendar" id="Selected_Calendar">
                                <option value="0">Choose Calendar :</option>
                                <option v-for="option in Calendar" :value="option.id_calendar" :key="option.id_calendar">{{
                                    option.name_calendar }}</option>
                            </select>
                        </div>
                        <div class="AddInputBox">
                            <input @click="AddExistingCalendar" type="submit" value="Add" name="submit" />
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
                            <input type="file" id="fileInput" accept=".ics" @change="handleFileChange"
                                style="display: none;">
                            <div class="Create-planning-Btn" @click="openFileInput" style="margin-left: 33px;">{{
                                labelText
                            }}</div>
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
                                    <option value="blue"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #0084ff;" />
                                        Blue</option>
                                    <option value="purple"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #d400ff;" />
                                        Purple</option>
                                    <option value="pink"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff00ae;" />
                                        Pink</option>
                                    <option value="red"><font-awesome-icon icon="fa-solid fa-circle"
                                            style="color: #ff0033;" />
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
                            <input @click="addCreatePlanning" type="submit" value="Add" name="submit" />
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
                            <input @click="deleteTask" style="margin-left: 0px;" type="submit" value="Delete"
                                name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>



        <!--<div id="CreateCalendarEvent" class="modal1">
            <div class="modal-content-create">
                <span class="close" @click="CloseCreateCalendarEvent">&times;</span>
                <h1 class="modal-Title" style="margin-bottom : 40px;">Your new Calendar</h1>
                <div class="modal-center1">

                    <input type="text" id="fname" name="fname" class="new-task-input" placeholder="Event Name"><br>
                    <div class="New-list-element1" style="width: 28%;">
                        <div class="FormBox">
                            <div class="FormContainer">
                                <div class="Form-banner-container">
                                    <div class="loginForm">
                                        <h2>Added Tasks</h2>
                                        <p class="Form-presentation"> <br> The following tasks <i class="fa fa-bold"
                                                aria-hidden="true">were fit</i> in the newly generated
                                            algorithm.<br><br> If this is okay with you please <i class="fa fa-bold"
                                                aria-hidden="true">validate</i> below.<br><br> Otherwise, please check
                                            if
                                            you've entered too many tasks, or concurring tasks and choose to <i
                                                class="fa fa-bold" aria-hidden="true">reselect</i> below. <br><br></p>
                                        <div class="created-tasks-container">
                                            <div class="created-tasks-new-container">
                                                <div class="created-tasks-new" style="--color:#F291BB;">
                                                    <p class="created-tasks-title">
                                                        SoirÃ©e d'anniv hihi
                                                    </p>

                                                    <p class="created-tasks-title">
                                                        5H
                                                    </p>
                                                </div>
                                                
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
                                                
                                            </div>
                                        </div>
                                        <button class="Create-planning-Btn" id="addCalendar">
                                            Generate Planning
                                        </button>
                                         <div >
                                    <input type="submit" value="" name="btnUpdate" />
                                </div> 
                                        <p class="forgotPswd MoveOn">
                                            Not done yet ?<btn id="AddNewTask">Add Event</btn>
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="delete-list-button">
                    <div class="AddTaskInputBox no">
                        <input @click="CreateCalendar" class="close" type="submit" value="Generate Planning !"
                            name="submit" />
                    </div>
                    <div class="AddTaskInputBox no">
                        <input @click="DeleteCalendar" style="margin-left: 0px;" type="submit" value="Go Back To Review ->"
                            name="submit" />
                    </div>
                </div>
            </div>
        </div>-->

        <div class="create-calendar-event1" id="CreateCalendarEvent">
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
                                        <div class="created-tasks-container" v-for="(event, index) in events" :key="index">
                                            <div :class='"created-tasks-new " + event.color'>
                                                <p class="created-tasks-title">{{ event.name_event }}</p>
                                                <p class="created-tasks-title">{{ Math.floor(event.length / 60) }}H</p>
                                            </div>
                                        </div>

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
                                    <div v-for="(week, index) in EventByWeek" :key="index">
                                        <div :class='"day " + week.day'>
                                            <div class="date">
                                                <p class="date-num">{{ week.day_nb }}</p>
                                                <p class="date-day">{{ week.day }}</p>
                                            </div>
                                            <div class="events">
                                                <div class="events" v-for="(cal, Calindex) in week.events" :key="Calindex">

                                                    <div class="events" v-for="(event, Calindex) in cal.event"
                                                        :key="Calindex">
                                                        <div :id='event.id_calendar + "-" + event.id_event'
                                                            :class='"event start-" + event.f_start_date + " end-" + event.f_end_date + " " + event.color + " calendar-" + week.color_calendar'>
                                                            <p class="calendar-title">{{ event.name_event }}</p>
                                                            <p class="calendar-time">
                                                                {{ event.start_time }} - {{ event.end_time }}</p>
                                                        </div>
                                                    </div>
                                                </div>
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
                        <input class="close" type="submit" value="Generate Planning !" name="submit" @click = "CreateCalendar" />
                    </div>
                    <div class="AddTaskInputBox no">
                        <input style="margin-left: 0px;" type="submit" value="Go Back To Review ->" @click = "DeleteCalendar" name="submit" />
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
            SelectedEventName: '',
            SelectedDuration: '0',
            SelectedDate: '',
            SelectedType: '0',
            SelectedDelete: "",
            SelectedFrequence: 'first',
            SelectedImportance: '0',
            daysOfWeek: [],
            EventByWeek: [],
            days: ['sun', 'mon', 'tues', 'wed', 'thurs', 'fri', 'sat'],
            CalColor: "0",
            CalendarName: "",
            Processed: [],
            Calendar: [],
            ProcessedList: [],
            message: '',
            events: [],
            Tasks: { color_calendar : "white", id_calendar: 0, events: [] },
            showAlert: false,
            invalidField: '',
            Failed : []
        }
    },
    methods: {
        CreateCalendar() {
            const token = localStorage.getItem('token');
            fetch("api/api/algorithm_confirm",
                {
                    method: 'GET',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    }
                })
            window.location.href = "/calendar-page";
        },
        DeleteCalendar() {
            const token = localStorage.getItem('token');
            fetch("api/api/algorithm_cancel",
                {
                    method: 'GET',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    }
                })
            this.CloseCreateCalendarEvent()
        },
        ValidateTime(field) {
            const dateTime = this[field];
            const time = dateTime.slice(11, 16);
            console.log(time)
            if (time < "06:00" || time > "23:00") {
                this[field] = '';
                this.showAlert = true;
                this.invalidField = field;
            } else {
                this.showAlert = false;
                this.invalidField = '';
            }
        },

        AddEvent() {
            if (
                this.SelectedEventName == '' ||
                this.SelectedDuration == '0' ||
                this.SelectedType == '0' ||
                this.SelectedFrequence == 'first' ||
                this.SelectedImportance == '0'
            ) {
                this.message = 'You must fill all the required fields';
                console.log(this.message);
                console.log(
                    this.SelectedEventName,
                    this.SelectedDuration,
                    this.SelectedDate,
                    this.SelectedType,
                    this.SelectedFrequence,
                    this.SelectedImportance
                );
            } else {
                // Access the v-model variables and perform necessary transformations/actions
                const eventName = this.SelectedEventName;
                const durationHours = parseInt(this.SelectedDuration);
                const durationMinutes = durationHours * 60; // Convert hours to minutes

                // Transform the SelectedDate value to the desired format (yyyy-mm-dd hh:mm:ss)
                const selectedDateTime = new Date(this.SelectedDate);
                const year = selectedDateTime.getFullYear();
                const month = ('0' + (selectedDateTime.getMonth() + 1)).slice(-2);
                const day = ('0' + selectedDateTime.getDate()).slice(-2);
                const hours = ('0' + selectedDateTime.getHours()).slice(-2);
                const minutes = ('0' + selectedDateTime.getMinutes()).slice(-2);
                const seconds = ('0' + selectedDateTime.getSeconds()).slice(-2);


                const type = this.SelectedType;
                const frequence = this.SelectedFrequence;
                const importance = this.SelectedImportance;
                if (this.SelectedDate == "") {
                    var transformedDate = "";
                } else {
                    transformedDate = `${year}-${month}-${day} ${hours}:${minutes}:${seconds}`;
                }

                this.Tasks.events.push(
                    {
                        'name': eventName,
                        'description': "Description",
                        "start_date": transformedDate,
                        'duration': durationHours,
                        'length': durationMinutes,
                        'color': type,
                        "priority_level": importance,
                        tasks: []

                    })

                console.log("Tasks pulled ",this.Tasks)
                // Display a message when it is successfully added
                this.message = 'Information successfully added !';
                console.log(this.message);

                // Display the unused variables in the console
                console.log(
                    eventName,
                    durationMinutes,
                    transformedDate,
                    type,
                    frequence,
                    importance
                );

                // Clear the input fields after processing
                this.SelectedEventName = '';
                this.SelectedDuration = '0';
                this.SelectedDate = '';
                this.SelectedType = '0';
                this.SelectedFrequence = 'first';
                this.SelectedImportance = '0';
                this.showAlert = false;
                this.invalidField = '';
            }
        },
        AddExistingCalendar() {
            this.ClosemyModalPlus()
            const cal = this.Calendar.find(item => item.id_calendar === this.SelectedCalendar)
            this.Tasks.id_calendar = this.SelectedCalendar;
            this.Tasks.color_calendar = cal ? cal.color_calendar : null;
            console.log(this.Tasks)
            console.log("Tasks pulled ",this.Tasks)
            const token = localStorage.getItem('token');
            fetch('api/api/algorithm_loaded', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    Authorization: 'Bearer ' + token,
                },
                body: JSON.stringify(this.Tasks)
            }).then((response) => {

                if (response.ok) {
                    this.message = '';

                    return response.json()
                } else {
                    return response.json().then(error => {
                        throw new Error(JSON.stringify(error));
                    });
                }

            }).then((json) => {
                this.Processed = json.processed
                this.Failed = json.failed
                console.log(json)
                return json.processed
            }).then((process) => {
                console.log(process)
                this.getEventByWeek();
                this.OpenCreateCalendarEvent(this.Failed);
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
        },
        CreateACalendar() {
            if (this.CalendarName == '' || this.CalColor == "0") {
                this.message = 'You must fill all the required fields'
            } else {

                this.CloseCreateCalendarModal();
                this.ClosemyModalPlus();

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
                        if (response.ok) {
                            this.message = '';
                            return response.json();
                        } else {
                            return response.json().then(error => {
                                throw new Error(JSON.stringify(error));
                            });
                        }
                    })
                    .then((eventData) => {
                        console.log(eventData)
                        this.Tasks.id_calendar = eventData.task.id_calendar;
                        this.Tasks.color_calendar = eventData.task.color;

                        console.log("Tasks pulled ",this.Tasks)

                        fetch('api/api/algorithm_loaded', {
                            method: 'POST',
                            headers: {
                                'Content-Type': 'application/json',
                                Authorization: 'Bearer ' + token,
                            },
                            body: JSON.stringify(this.Tasks)
                        }).then((response) => {

                            if (response.ok) {
                                this.message = '';
                                return response.json()
                            } else {
                                return response.json().then(error => {
                                    throw new Error(JSON.stringify(error));
                                });
                            }

                        }).then((json) => {
                            this.Processed = json.processed;
                            this.Failed = json.failed;
                            console.log(this.Processed);
                            console.log(json)
                            return json.processed
                        }).then((process) => {
                            console.log(process)
                            this.getEventByWeek()
                            this.OpenCreateCalendarEvent(this.Failed)
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
            }
        },
        OpenCreateCalendarModal() {
            this.getProcessed()
            document.getElementById("CreateCalendarModal").style.display = "block";
        },
        CloseCreateCalendarModal() {
            document.getElementById("CreateCalendarModal").style.display = "none";
            this.message = "";
        },
        OpenmyModaladdNewCalendar() {
            document.getElementById("myModaladdNewCalendar").style.display = "block";
        },
        ClosemyModaladdNewCalendar() {
            document.getElementById("myModaladdNewCalendar").style.display = "none";
            this.message = "";
        },
        OpenmyModalPlus() {
            document.getElementById("myModalPlus").style.display = "block";
        },
        ClosemyModalPlus() {
            document.getElementById("myModalPlus").style.display = "none";
            this.message = "";
        },
        OpenImportCalendarModal() {
            document.getElementById("ImportCalendarModal").style.display = "block";
        },
        CloseImportCalendarModal() {
            document.getElementById("ImportCalendarModal").style.display = "none";
            this.message = "";
        },
        OpenmyModalEventDelete(id) {

            this.SelectedDelete = id;
            console.log(id)
            console.log(this.Tasks.events)
            document.getElementById("myModalEventDelete").style.display = "block";
        },
        ClosemyModalEventDelete() {
            document.getElementById("myModalEventDelete").style.display = "none";
            this.message = "";
        },
        deleteTask() {
            
            this.Tasks.events.splice(this.SelectedDelete, 1)
            document.getElementById("myModalEventDelete").style.display = "none";
        },
        cancelDeleteTask() {
            document.getElementById("myModalEventDelete").style.display = "none";
        },
        OpenCreateCalendarEvent(events) {
            this.events = events;
            document.getElementById("CreateCalendarEvent").style.display = "block";
            console.log("List of events: ", this.events)
        },
        CloseCreateCalendarEvent() {
            document.getElementById("CreateCalendarEvent").style.display = "none";
            this.message = "";
        },
        AddToCalendarFromAddANewCalendar() {
            this.OpenmyModalPlus();
            this.ClosemyModaladdNewCalendar();
        },
        NewBlankCalendarFromAddANewCalendar() {
            this.OpenCreateCalendarModal();
            this.ClosemyModaladdNewCalendar();
        },
        addAddToCalendar() {
            this.OpenCreateCalendarEvent(this.Failed);
            this.ClosemyModalPlus();
        },
        addCreatePlanning() {
            this.CreateACalendar();
            this.CloseCreateCalendarModal();
        },
        getWeek(date) {
            const year = parseInt(date.slice(0, 4));
            const month = parseInt(date.slice(5, 7));
            const day = parseInt(date.slice(8));
            const weekNumber = this.getISOWeekNumber(year, month, day) - 1;
            const formattedWeek = `${year}-W${weekNumber.toString().padStart(2, '0')}`;

            return formattedWeek;
        },
        getDaysOfWeek() {
            this.daysOfWeek = []
            const currentDate = new Date()
            const day = currentDate.getDay()
            const day_nb = currentDate.getDate()
            for (let i = 0; i < 7; i++) {

                this.daysOfWeek.push(day_nb + i);
            }
            this.days = this.days.slice(day).concat(this.days.slice(0, day))
            console.log(this.day)
            console.log(this.days)

        },
        GetTime(Date) {
            const time = Date.slice(-8);
            const hours = time.split(":")[0];
            let minutes = time.split(":")[1];

            if (minutes === 60) {
                minutes = 0;
            }

            const formattedMinutes = (minutes !== 0) ? minutes.toString() : "00";
            const formattedTime = `${hours}-${formattedMinutes}`;
            return formattedTime;

        },
        addDurationToTime(time, durationInMinutes) {

            const [hours, minutes] = time.split(":").map(Number);
            const timeInMinutes = hours * 60 + minutes;
            const endTimeInMinutes = timeInMinutes + parseInt(durationInMinutes);
            const resultingHours = Math.floor(endTimeInMinutes / 60);
            const resultingMinutes = endTimeInMinutes % 60;
            const endTime = `${String(resultingHours).padStart(2, "0")}:${String(resultingMinutes).padStart(2, "0")}:00`;

            return endTime;
        },
        format_sd(date) {
            const Start_Date = new Date(date);


            const year = Start_Date.getFullYear();
            const month = Start_Date.getMonth() + 1;
            const day = Start_Date.getDate();
            const adjustedDate = `${year}-${month < 10 ? '0' + month : month}-${day < 10 ? '0' + day : day}`;

            const hours = Start_Date.getUTCHours();
            const minutes = Start_Date.getUTCMinutes();
            const seconds = Start_Date.getUTCSeconds();
            const adjustedTime = `${hours < 10 ? '0' + hours : hours}:${minutes < 10 ? '0' + minutes : minutes}:${seconds < 10 ? '0' + seconds : seconds}`;


            const converted_date = `${adjustedDate} ${adjustedTime}`;

            return converted_date;
        },
        getProcessed() {

            this.ProcessedList = this.Processed.map((ev) => {

                if (ev.start_date.includes('Z')) {
                    ev.start_date = this.format_sd(ev.start_date)
                }
                console.log(this.GetTime(ev.start_date))
                console.log(this.GetTime(this.addDurationToTime(ev.start_date.slice(-8), ev.length)))
                console.log(this.addDurationToTime(ev.start_date.slice(-8), ev.length))
                return {
                    name_calendar: ev.name_calendar,
                    id_calendar: ev.id_calendar,
                    calendar_color: ev.calendar_color,
                    name_event: ev.name_event,
                    start_time: this.GetTime(ev.start_date),
                    start_date: ev.start_date,
                    end_time: this.GetTime(this.addDurationToTime(ev.start_date.slice(-8), ev.length)),
                    end_date: this.addDurationToTime(ev.start_date.slice(-8), ev.length),
                    length: ev.length,
                    color: ev.color,
                    day: this.getDay(ev.start_date),
                    day_nb: ev.start_date.substr(8, 2),
                    f_start_date: this.formattedTime(ev.start_date),
                    f_end_date: this.formattedTime(this.addDurationToTime(ev.start_date.slice(-8), ev.length))


                }
            })

            return this.ProcessedList
        },
        formattedTime(Date) {
            const time = Date.slice(-8);
            const hours = time.split(":")[0];
            let minutes = time.split(":")[1];

            minutes = Math.round(minutes / 15) * 15;

            if (minutes === 60) {
                minutes = 0;
            }

            const formattedMinutes = (minutes !== 0) ? minutes.toString() : "00";
            const formattedTime = `${hours}-${formattedMinutes}`;
            return formattedTime;

        },
        getDay(dateString) {
            var date = new Date(dateString);
            var dayOfWeek = date.getDay();

            var day = this.days[dayOfWeek - 1];

            return day;
        },
        async getEventByWeek() {

            const eventsForWeek = {};

            await this.daysOfWeek
            await this.getProcessed()
            console.log(this.ProcessedList)
            for (const [index, day] of this.days.entries()) {
                const day_nb = this.daysOfWeek[index];
                eventsForWeek[day] = {
                    day: day,
                    day_nb: day_nb,
                    color_calendar : "",
                    events: {},
                };
            }

            this.ProcessedList.forEach((event) => {

                const day = event.day;
                const id_cal = event.id_calendar;
                
                if (!eventsForWeek[day].events[id_cal]) {
                    eventsForWeek[day].events[id_cal] = {
                        event: [],
                    };
                }
                eventsForWeek[day].color_calendar = this.Tasks.color_calendar;
                eventsForWeek[day].events[id_cal].event.push(event);
            })



            this.EventByWeek = eventsForWeek;
            console.log(this.EventByWeek)
            return eventsForWeek;
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
                this.calendar = JSON.parse(JSON.stringify(data.calendars));
            } catch (error) {
                console.error(error.message);
            }
        },
        async initializePage() {

            await this.GetCalendar();

            this.Calendar = this.calendar.map((calendar) => {

                return {
                    name_calendar: calendar.name_calendar,
                    id_calendar: calendar.id_calendar,
                    color_calendar : calendar.color
                };
            })
        },
        /*
        handleFileChange(event) {
            const file = event.target.files[0];
            if (file) {
                this.labelText = file.name;
                this.selectedFile = file;
            } else {
                this.labelText = 'No file selected';
                this.selectedFile = null;
            }
        },
        UploadFile() {
            console.log(this.selectedFile, this.CalendarName, this.CalColor)
            if (this.selectedFile == null || this.CalendarName == "" || this.CalColor == "0") {
                this.message = "Please fill all the fields";
            } else {
                const token = localStorage.getItem('token');
                const formData = new FormData();
                formData.append('icsFile', this.selectedFile);
                formData.append('name_calendar', this.CalendarName);
                formData.append('color_calendar', this.CalColor);
                var request = new XMLHttpRequest();
                request.open('POST', '/api/api/icsimport');
                request.setRequestHeader('Authorization', 'Bearer ' + token);
                request.onload = function () {
                    if (request.status >= 200 && request.status < 400) {
                        this.message = request.responseText;
                    } else {
                        this.message = 'Request failed with status', request.status;
                    }
                    request.onerror = function () {
                        this.message = 'Request failed';
                    }
                }
                request.send(formData);
                this.Reload();
            }
        },
        */
    },
    beforeMount() {
        this.initializePage().then(() => {
            const currentWeek = new Date().toISOString().slice(0, 10)
            this.getEventByWeek(currentWeek);
            console.log(this.Calendar)

        });
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