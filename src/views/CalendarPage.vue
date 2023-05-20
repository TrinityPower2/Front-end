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
        <div class="Calendar-page-container">
            <div class="calendar-sidebar-container">
                <button :class='"Your-calendar-button-" + cal.calendar_color' v-for="(cal, index) in Calendar" :key="index"
                    @click="DisplayCalendar(cal.id_calendar)">
                    <p class="your-calendar-letter">{{ cal.name_calendar[0] }}</p>
                </button>
                <div class="Add-calendar-sidebar" @click="OpenmyModalNewCalendar"><font-awesome-icon id="AddCalendar"
                        icon="fa-solid fa-plus" size="lg" style="color:rgba(47, 43, 44, 0.648)" />
                </div>
            </div>
            <div class="calendar-display-container">
                <div class="calendar-top-buttons">
                    <div class="choose-week">
                        <div>
                            <input ref="weekInput" id="party" type="week" class="Create-planning-Btn calendar-dark-btn"
                                v-model="selectedWeek" @change="handleWeekChange">
                        </div>
                        <font-awesome-icon icon="fa-solid fa-angle-left" class="arrow-left-calendar"
                            @click="ChangeWeek(-1)" />
                        <font-awesome-icon icon="fa-solid fa-angle-right" class="arrow-left-calendar"
                            @click="ChangeWeek(+1)" />
                    </div>
                    <div class="buttons-calendar-container">
                        <button class="Create-planning-Btn calendar-dark-btn" id="deleteCalendar" @click="OpenNewCalendar">
                            Add Event
                        </button>
                        <button class="Create-planning-Btn calendar-dark-btn" id="addCalendar" @click="OpenDeleteCalendar">
                            Delete Calendar
                        </button>
                        <button class="Create-planning-Btn calendar-dark-btn" id="addCalendar" @click="OpenUpdateCalendar">
                            Update Calendar
                        </button>
                    </div>
                </div>
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
                            <div v-for="(cal, index) in EventByWeek" :key="index">
                                <div :class='"day " + cal.day'>
                                    <div class="date">
                                        <p class="date-num">{{ cal.day_nb }}</p>
                                        <p class="date-day">{{ cal.day }}</p>
                                    </div>
                                    <div class="events">
                                        <div class="events" v-for="(event, Evindex) in cal.events" :key="Evindex"
                                            :id="`calendar-${index}`" v-show="shouldDisplayCalendar(cal.id_cal)">
                                            <div :id='cal.id_cal + "-" + event.event.id_event'
                                                :class='"event start-" + event.event.f_start_date + " end-" + event.event.f_end_date + " " + event.event.color + " calendar-" + cal.calendar_color'
                                                @click="OpenLoadCalendarModal(event.event.id_event, cal.id_cal)">
                                                <p class="calendar-title">{{ event.event.name_event }}</p>
                                                <p class="calendar-time">
                                                    {{ event.event.start_date.slice(-8).replace(/(\d+)-(\d+)/, "$1H$2") }} -
                                                    {{ event.event.end_date.slice(-8).replace(/(\d+)-(\d+)/, "$1H$2") }}</p>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="NewCalendarModal" class="modal1">
                <div class="modal-content-create" style="max-width:800px;">
                    <span class="close" @click="CloseNewCalendar">&times;</span>
                    <h1 class="modal-Title" style="margin-bottom: 40px">New Event</h1>
                    <br>
                    <div class="modal-center">
                        <input v-model="SelectedEventName" type="text" id="fname" name="fname" class="new-task-input"
                            placeholder="Event Name" /><br />
                        <div class="custom-select">
                            <select class="select-items" v-model="SelectedCalendar" id="Selected_Calendar">
                                <option value="0">Choose Calendar :</option>
                                <option v-for="option in Calendar" :value="option.id_calendar" :key="option.id_calendar">{{
                                    option.name_calendar }}</option>
                            </select>
                        </div>
                    </div>
                    <br>
                    <div class="modal-center1">
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-regular fa-calendar-days" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />

                            <div class="custom-select" id="Time-Task">
                                <input class="select-items" type="date" id="day" name="day-task" v-model="SelectedDate"
                                    min="2023-04-01" max="2028-12-31">
                            </div>
                        </div>
                        <div class="New-list-element1">

                            <font-awesome-icon icon="fa-regular fa-hourglass-half" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="Timeslots-choice">
                                <div class="custom-select" id="Time-Task">
                                    <input class="select-items" type="time" id="day" name="day-task" v-model="StartTime"
                                        min="6:00" max="23:00">
                                </div>
                                <div class="custom-select" id="Time-Task">
                                    <input class="select-items" type="time" id="day" name="day-task" v-model="EndTime"
                                        min="6:00" max="23:00">
                                </div>
                            </div>
                        </div>

                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-palette" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="custom-select">
                                <select class="select-items" v-model="SelectedType">
                                    <option value="0">Type of event :</option>
                                    <option value="red">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #00ff88" />
                                        Party
                                    </option>
                                    <option value="yellow">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff" />
                                        Project
                                    </option>
                                    <option value="blue">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #d400ff" />
                                        Work
                                    </option>
                                    <option value="green">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae" />
                                        Health
                                    </option>
                                    <option value="purple">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033" />
                                        Holiday
                                    </option>
                                    <option value="pink">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff8800" />
                                        Family
                                    </option>
                                    <option value="orange">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffdd00" />
                                        Class
                                    </option>
                                    <option value="white">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffffff" />
                                        Friends
                                    </option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-repeat" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="custom-select">
                                <select class="select-items" v-model="SelectedFrequence">
                                    <option value="first">Frequence :</option>
                                    <option value="6">Every day</option>
                                    <option value="5">Every 2 days</option>
                                    <option value="4">Every 3 days</option>
                                    <option value="3">Weekly</option>
                                    <option value="2">Twice a day</option>
                                    <option value="0">None</option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-circle-exclamation" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="custom-select">
                                <select class="select-items" v-model="SelectedImportance">
                                    <option value="0">Importance :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                            </div>
                        </div>
                        <br>
                        <div class="New-list-element2" style="margin-left: 14%">
                            <font-awesome-icon icon="fa-solid fa-list-check" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="Add-another-container">
                                <div class="Add-another-task">
                                    <div class="new-task-create">
                                        <label class="task-container" style="margin-left: 0%;">
                                            <input type="checkbox" v-model="taskChecked" />
                                            <span class="checkmark"></span>
                                        </label>
                                        <input type="text" v-model="taskInput" class="new-task-input"
                                            placeholder="..." /><br>
                                        <div class="custom-select">
                                            <select id="ImportanceTask" class="select-items"
                                                v-model="SelectedTaskImportance">
                                                <option value="0">Choose Importance :</option>
                                                <option value="1">Urgent</option>
                                                <option value="2">Important</option>
                                                <option value="3">Medium</option>
                                                <option value="4">Minor</option>
                                                <option value="5">Do Later</option>
                                            </select>
                                        </div>
                                    </div>

                                    <div class="new-task-appear">
                                        <div v-for="(new_task, index) in AddTasks" :key="index"
                                            :id="'CloseTdTaskC-' + index" class="CloseTask-container">

                                            <div class="new-task-create2" :id="'CloseTdTask-' + index">
                                                <label class="task-container" style="margin-left: 0%;">
                                                    <input type="checkbox" :id="'taskChecked_' + index"
                                                        v-model="taskCheckedArray[index]" />
                                                    <span class="checkmark"></span>
                                                </label>
                                                <input type="text" :id="'taskInput_' + index"
                                                    v-model="taskInputArray[index]" class="new-task-input"
                                                    placeholder="..." /><br>
                                                <div class="custom-select">
                                                    <select :id="'ImportanceTask-' + index" class="select-items"
                                                        v-model="selectedImportanceArray[index]">
                                                        <option value="0">Choose Importance :</option>
                                                        <option value="1">Urgent</option>
                                                        <option value="2">Important</option>
                                                        <option value="3">Medium</option>
                                                        <option value="4">Minor</option>
                                                        <option value="5">Do Later</option>
                                                    </select>
                                                </div>
                                                <button :id="'CloseTask-' + index" class="CloseTask"
                                                    @click="DeleteTdTask(index)"><font-awesome-icon icon="fa-solid fa-plus"
                                                        size="sm"
                                                        style="transform:rotate(45deg); margin-left: 15px;" /></button>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="new-task-create" style="margin-top: 8px;" @click="addTask()">
                                        <font-awesome-icon icon="fa-solid fa-plus" size="sm" />
                                        <p>New Task</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="message"> {{ message }}</div><br>
                        <div style="width: 90%; display: flex; justify-content: center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input type="submit" value="Add" name="submit" @click="AddEvent" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="LoadCalendarModal" class="modal1">
            <div class="modal-content-create" style="max-width:800px;">
                <span class="close" @click="CloseLoadCalendarModal">&times;</span>
                <h1 class="modal-Title" style="margin-bottom: 40px">Edit Event</h1>
                <div class="modal-center1">
                    <input v-model="SelectedEventName" type="text" id="fname" name="fname" class="new-task-input"
                        placeholder="Event Name" /><br />
                    <div class="New-list-element1">
                        <font-awesome-icon icon="fa-regular fa-calendar-days" size="xl"
                            style="color: rgba(85, 84, 85, 0.986)" />

                        <div class="Timeslots-choice">
                            <div class="custom-select" id="Time-Task">
                                <input class="select-items" type="date" id="day" name="day-task" v-model="SelectedDate"
                                    min="2023-04-01" max="2028-12-31">
                            </div>
                        </div>
                    </div>
                    <div class="New-list-element1">

                        <font-awesome-icon icon="fa-regular fa-hourglass-half" size="xl"
                            style="color: rgba(85, 84, 85, 0.986)" />
                        <div class="Timeslots-choice">
                            <div class="custom-select" id="Time-Task">
                                <input class="select-items" type="time" id="day" name="day-task" v-model="StartTime"
                                    min="6:00" max="23:00">
                            </div>
                            <div class="custom-select" id="Time-Task">
                                <input class="select-items" type="time" id="day" name="day-task" v-model="EndTime"
                                    min="6:00" max="23:00">
                            </div>
                        </div>
                    </div>

                    <div class="New-list-element1">
                        <font-awesome-icon icon="fa-solid fa-palette" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
                        <div class="custom-select">
                            <select class="select-items" v-model="SelectedType">
                                <option value="0">Type of event :</option>
                                <option value="red">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #00ff88" />
                                    Party
                                </option>
                                <option value="yellow">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff" />
                                    Project
                                </option>
                                <option value="blue">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #d400ff" />
                                    Work
                                </option>
                                <option value="green">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae" />
                                    Health
                                </option>
                                <option value="purple">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033" />
                                    Holiday
                                </option>
                                <option value="pink">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff8800" />
                                    Family
                                </option>
                                <option value="orange">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffdd00" />
                                    Class
                                </option>
                                <option value="white">
                                    <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffffff" />
                                    Friends
                                </option>
                            </select>
                        </div>
                    </div>
                    <div class="New-list-element1">
                        <font-awesome-icon icon="fa-solid fa-repeat" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
                        <div class="custom-select">
                            <select class="select-items" v-model="SelectedFrequence">
                                <option value="6">Every day</option>
                                <option value="5">Every 2 days</option>
                                <option value="4">Every 3 days</option>
                                <option value="3">Weekly</option>
                                <option value="2">Twice a day</option>
                                <option value="0">None</option>
                            </select>
                        </div>
                    </div>
                    <!-- <div class="New-list-element1">
                            <font-awesome-icon icon="fa-regular fa-bell" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
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
                        </div> -->
                    <div class="New-list-element1">
                        <font-awesome-icon icon="fa-solid fa-circle-exclamation" size="xl"
                            style="color: rgba(85, 84, 85, 0.986)" />
                        <div class="custom-select">
                            <select class="select-items" v-model="SelectedImportance">
                                <option value="0">Importance :</option>
                                <option value="1">Urgent</option>
                                <option value="2">Important</option>
                                <option value="3">Medium</option>
                                <option value="4">Minor</option>
                                <option value="5">Do Later</option>
                            </select>
                        </div>
                    </div>
                    <div class="New-list-element" style="margin-left: 14%">
                        <font-awesome-icon icon="fa-solid fa-list-check" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
                        <!-- <div class="custom-select create-select">
                                <select>
                                    <option value="0">ToDo List :</option>
                                </select>
                            </div> -->
                    </div>
                    <div class="Add-another-container">
                        <div class="Add-another-task">
                            <div class="new-task-create">
                                <label class="task-container" style="margin-left: 0%">
                                    <input type="checkbox" />
                                    <span class="checkmark"></span>
                                </label>
                                <input type="text" id="fname" name="fname" class="new-task-input" placeholder="My Task"
                                    style="margin-right: 3%; width:80%;" /><br />
                                <font-awesome-icon icon="fa-solid fa-plus" size="s" style="transform:rotate(45deg)" />
                            </div>
                            <div class="new-task-create">
                                <font-awesome-icon icon="fa-solid fa-plus" size="s" @click="addTask" />
                                <p>Add Task</p>
                            </div>
                        </div>
                    </div>
                    <div style="
              width: 90%;
              display: flex;
              justify-content: center;
              margin-top: 50px;
            ">
                        <div class="AddTaskInputBox">
                            <input @click="OpenDeleteEvent" style="margin-left: 0px;" type="submit" value="Delete"
                                name="submit" />
                        </div>
                        <div class="AddTaskInputBox">
                            <input @click="UpdateEvent" type="submit" value="Update" name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="myModalNewCalendar" class="modal">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close" @click="ClosemyModalNewCalendar">&times;</span>
                <h1 class="modal-Title">Add New Calendar</h1>
                <div class="modal-center">
                    <p style="margin-top: 50px;">How would you like to create you new calendar ?</p>
                    <div class="delete-list-button">
                        <div class="AddTaskInputBox no">
                            <input class="close" type="submit" @click="OpenImportCalendarModal" value="Import Calendar"
                                name="submit" id="import-pop-up" />
                        </div>
                        <div class="AddTaskInputBox no">
                            <div class="pop-up-route-container">
                                <router-link class="pop-up-route" to="/create-calendar-page">New Optimized
                                    Calendar</router-link>
                            </div>
                            <!-- <input class="close" type="submit" value="New Optimized Calendar" name="submit" /> -->
                        </div>
                        <div class="AddTaskInputBox no">
                            <input @click="OpenCreateCalendarModal" style="margin-left: 0px;" type="submit"
                                value="New Blank Calendar" name="submit" id="blankCalendar" />
                        </div>
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
                        <input type="file" id="fileInput" accept=".ics" @change="handleFileChange" style="display: none;">
                        <div class="import-file" @click="openFileInput">{{ labelText }}</div>
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
                            <input @click="CreateCalendar" type="submit" value="Create Calendar" name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <div id="UpdateCalendarModal" class="modal1">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close" @click="CloseUpdateCalendar">&times;</span>
                <h1 class="modal-Title" style="margin-bottom : 40px;">Update Planning</h1>

                <div class="modal-center">
                    <div class="custom-select">
                        <select class="select-items" v-model="SelectedCalendar" id="Selected_Calendar" @click="Fill()">
                            <option value="0">Choose Calendar :</option>
                            <option v-for="option in Calendar" :value="option.id_calendar" :key="option.id_calendar">{{
                                option.name_calendar }}</option>
                        </select>
                    </div>
                    <div class="New-list-element" v-show="SelectedCalendar !== '0'">
                        <div class="new-list-desc">
                            Name of Calendar
                        </div>
                        <input v-model="CalendarName" type="text" id="fname" name="fname" class="new-task-input"
                            placeholder="Calendar Name" /><br />
                    </div>
                    <div class="New-list-element" v-show="SelectedCalendar !== '0'">
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
                    <div class="Form-banner-container-update" v-show="SelectedCalendar !== '0'">
                        <p class="Form-question">Do you want notification ?</p>
                        <div class="Switch-container">
                            <p class="Switch-label">YES</p>
                            <label class="switch">
                                <input type="checkbox" v-model="notificationEnabled" :value="true">
                                <span class="slider"></span>
                            </label>
                            <p class="Switch-label">NO</p>
                        </div>
                    </div>
                    <br><br>
                    <div class="message"> {{ message }}</div><br>
                    <div style="width:50%; display:flex; justify-content:center; margin-top: 50px;">
                        <div class="AddTaskInputBox">
                            <input @click="UpdateCalendar" type="submit" value="Update Calendar" name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="myEventDelete" class="modal">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close" @click="CloseDeleteEvent">&times;</span>
                <h1 class="modal-Title">Delete Event</h1>
                <div class="modal-center">
                    <p style="margin-top: 50px;">Are you sure you want to delete this Event ?</p>
                    <div class="delete-list-button">
                        <div class="AddTaskInputBox no">
                            <input @click="DeleteEvent" class="close" type="submit" value="Delete" name="submit" />
                        </div>
                        <div class="AddTaskInputBox no">
                            <input @click="CloseDeleteEvent" style="margin-left: 0px;" type="submit" value="Cancel"
                                name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="myCalendarDelete" class="modal1">
            <!-- Modal content -->
            <div class="modal-content1">
                <span class="close" @click="CloseDeleteCalendar">&times;</span>
                <h1 class="modal-Title">Delete Calendar</h1>
                <br><br>
                <div class="modal-center">
                    <div class="custom-select">
                        <select class="select-items" v-model="SelectedCalendar" id="Selected_Calendar">
                            <option value="0">Choose Calendar :</option>
                            <option v-for="option in Calendar" :value="option.id_calendar" :key="option.id_calendar">{{
                                option.name_calendar }}</option>
                        </select>
                    </div>
                    <p style="margin-top: 50px;">Are you sure you want to delete this Calendar ?</p>
                    <div class="delete-list-button">
                        <div class="AddTaskInputBox no">
                            <input @click="DeleteCalendar" class="close" type="submit" value="Delete" name="submit" />
                        </div>
                        <div class="AddTaskInputBox no">
                            <input @click="CloseDeleteCalendar" style="margin-left: 0px;" type="submit" value="Cancel"
                                name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"><font-awesome-icon
                icon="fa-solid fa-arrow-up" size="xs" style="color: #fff0fe" /></a>
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
                        <a href="https:www.linkedin.com/in/lou-brunesseaux-a843aa248"><font-awesome-icon
                                icon="fa-brands fa-linkedin-in" /></a>
                        <a href="mailto:loubruness@gmail.com"><font-awesome-icon icon="fa-brands fa-google" /></a>
                        <a href="https:github.com/loubruness"><font-awesome-icon icon="fa-brands fa-github" /></a>
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
    name: "CalendarPage",
    components: {
        DarkLightMode,
        UserMenu,
    },
    data() {
        return {
            SelectedCalendar: "0",
            SelectedImportance: "0",
            SelectedTaskImportance: "0",
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
            selectedImportanceArray: ["0"],
            taskInputArray: [''],
            taskInput: '',
            taskCheckedArray: [],
            taskChecked: '',
            notificationEnabled: false

        }
    },

    methods: {
        addTask() {
            const newTask = {
                checked: false,
                inputText: "",

            };
            this.selectedImportanceArray.push("0")
            this.AddTasks.push(newTask);

        },
        DeleteTdTask(index) {
            this.taskInputArray.splice(index, 1);
            this.selectedImportanceArray.splice(index, 1)
            this.taskCheckedArray.splice(index, 1)
            this.AddTasks.splice(index, 1)

        },
        OpenUpdateCalendar() {
            document.getElementById("UpdateCalendarModal").style.display = "block";
        },
        CloseUpdateCalendar() {
            document.getElementById("UpdateCalendarModal").style.display = "none";
            this.message = "";
        },
        async Fill() {

            const cal = await this.Calendar.find(calendar => calendar.id_calendar === this.SelectedCalendar);
            this.CalendarName = cal.name_calendar;
            this.CalColor = cal.calendar_color;
            this.notificationEnabled = cal.to_notify;
            console.log(cal.name_calendar);
            console.log(cal.calendar_color);
        },
        UpdateCalendar() {
            if (this.CalendarName == "" || this.CalColor == "0") {
                this.message = 'You must fill all the required fields'
            } else {
                const token = localStorage.getItem('token');
                fetch("api/api/calendar/" + this.SelectedCalendar,
                    {
                        method: 'PATCH',
                        headers: {
                            'Content-Type': 'application/json',
                            'Authorization': 'Bearer ' + token
                        },
                        body: JSON.stringify({ name_calendar: this.CalendarName, color: this.CalColor, to_notify: this.notificationEnabled })
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

            }
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
        DisplayCalendar(id) {
            if (this.visibleCalendars.includes(id)) {
                this.visibleCalendars = this.visibleCalendars.filter((calId) => calId !== id);
            } else {
                this.visibleCalendars.push(id);
            }
        },
        shouldDisplayCalendar(index) {
            return this.visibleCalendars.includes(index);
        },
        openFileInput() {
            document.getElementById('fileInput').click();
        },
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
        handleWeekChange() {

            this.selectedWeek = this.$refs.weekInput.value;
            localStorage.setItem("selectedWeek", this.selectedWeek);
            this.getEventByWeek(this.selectedWeek);
            this.getDaysOfWeek();
            console.log("SUIS JE TRIGGER ?")

        },

        ChangeWeek(operator) {

            const weekNumber = parseInt(this.selectedWeek.split('W')[1]);
            this.selectedWeek = this.selectedWeek.replace(`W${weekNumber}`, `W${weekNumber + operator}`);
            this.$refs.weekInput.value = this.selectedWeek
            localStorage.setItem("selectedWeek", this.selectedWeek);
            this.handleWeekChange();
            this.getDaysOfWeek();
        },
        getWeek(date) {
            const year = parseInt(date.slice(0, 4));
            const month = parseInt(date.slice(5, 7));
            const day = parseInt(date.slice(8));
            const weekNumber = this.getISOWeekNumber(year, month, day) - 1;
            const formattedWeek = `${year}-W${weekNumber.toString().padStart(2, '0')}`;

            return formattedWeek;
        },

        getISOWeekNumber(year, month, day) {

            const firstDayOfYear = new Date(year, 0, 1);
            const daysOffset = (firstDayOfYear.getDay() + 6) % 7;
            const adjustedDate = new Date(year, month - 1, day).getTime() + (daysOffset * 24 * 60 * 60 * 1000);
            const weekNumber = Math.ceil((((adjustedDate - firstDayOfYear.getTime()) / 86400000) + 1) / 7);

            return weekNumber;
        },

        OpenNewCalendar() {
            document.getElementById("NewCalendarModal").style.display = "block";
        },
        CloseNewCalendar() {
            document.getElementById("NewCalendarModal").style.display = "none";
            this.message = "";
        },
        GetEventByID() {
            const selectedCalendar = this.Calendar.find(calendar => calendar.id_calendar === this.CalendarIndex);
            if (selectedCalendar) {
                const selectedEvent = selectedCalendar.event.find(event => event.id_event === this.SelectedIndex);
                if (selectedEvent) {
                    this.SelectedCalendar = selectedCalendar.id_calendar;
                    this.SelectedEvent = selectedEvent.id_event;
                    this.SelectedType = selectedEvent.color;
                    this.SelectedFrequence = selectedEvent.to_repeat;
                    this.SelectedImportance = selectedEvent.priority_level;
                    this.SelectedEventName = selectedEvent.name_event;
                    this.SelectedDay = selectedEvent.day;
                    this.StartTime = selectedEvent.start_date.split(' ')[1];
                    this.SelectedDate = selectedEvent.start_date.split(' ')[0];
                    this.EndTime = selectedEvent.end_date;
                }
            }
        },
        OpenLoadCalendarModal(event, cal) {

            document.getElementById("LoadCalendarModal").style.display = "block";
            this.SelectedIndex = event
            this.CalendarIndex = cal
            this.GetEventByID()
        },
        CloseLoadCalendarModal() {
            document.getElementById("LoadCalendarModal").style.display = "none";
            this.SelectedType = "0";
            this.SelectedFrequence = "first";
            this.SelectedEventName = " "
            this.SelectedDay = "0";
            this.StartTime = "0"
            this.SelectedDate = "0"
            this.EndTime = "0"
            this.message = ""
        },
        OpenmyModalNewCalendar() {
            document.getElementById("myModalNewCalendar").style.display = "block";
        },
        ClosemyModalNewCalendar() {
            document.getElementById("myModalNewCalendar").style.display = "none";
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
        OpenDeleteCalendar() {
            document.getElementById("myCalendarDelete").style.display = "block";
            console.log("hihi ?")
        },
        CloseDeleteCalendar() {
            document.getElementById("myCalendarDelete").style.display = "none";
        },
        DeleteCalendar() {
            const token = localStorage.getItem('token');

            fetch("api/api/calendar/" + this.SelectedCalendar,
                {
                    method: 'DELETE',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    },
                })
                .then((response) => {
                    if (response.ok) {
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
            this.SelectedCalendar = "0";
            this.Reload();
        },
        OpenEvent() {
            document.getElementById("event").style.display = "block";
        },
        CloseEvent() {
            document.getElementById("event").style.display = "none";
            this.message = "";
            this.SelectedType = "0";
            this.SelectedFrequence = "first";
            this.SelectedEventName = " "
            this.SelectedDay = "0";
            this.StartTime = "0"
            this.SelectedDate = "0"
            this.EndTime = "0"
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
                this.event = JSON.parse(JSON.stringify(data.list));
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
                this.calendar = JSON.parse(JSON.stringify(data.calendars));
            } catch (error) {
                console.error(error.message);
            }
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
        getDaysOfWeek() {
            this.daysOfWeek = []

            const [year, week] = this.selectedWeek.split('-W');
            const startDate = new Date(year, 0, 1);
            const firstMonday = startDate.getDate() + (7 - startDate.getDay() + 1) % 7;
            const firstDayOfWeek = new Date(year, 0, firstMonday + (week - 1) * 7);
            for (let i = 0; i < 7; i++) {
                const date = new Date(firstDayOfWeek.getTime() + i * 24 * 60 * 60 * 1000);
                this.daysOfWeek.push(date.getDate());
            }

        },
        getDay(dateString) {
            var date = new Date(dateString);
            var dayOfWeek = date.getDay();

            var day = this.days[dayOfWeek - 1];

            return day;
        },
        async initializePage() {

            await this.GetEvent();
            await this.GetCalendar();

            this.Calendar = this.calendar.map((calendar) => {
                return {
                    name_calendar: calendar.name_calendar,
                    id_calendar: calendar.id_calendar,
                    calendar_color: calendar.color,
                    event: this.event.filter(event => event.id_calendar === calendar.id_calendar).map(ev => {
                        return {
                            id_event: ev.id_event,
                            name_event: ev.name_event,
                            description: ev.description,
                            priority_level: ev.priority_level,
                            start_time: this.GetTime(ev.start_date),
                            start_date: ev.start_date,
                            end_time: this.GetTime(this.addDurationToTime(ev.start_date.slice(-8), ev.length)),
                            end_date: this.addDurationToTime(ev.start_date.slice(-8), ev.length),
                            length: ev.length,
                            to_notify: ev.to_notify,
                            movable: ev.movable,
                            to_repeat: ev.to_repeat,
                            color: ev.color,
                            day: this.getDay(ev.start_date),
                            day_nb: ev.start_date.substr(8, 2),
                            week: this.getWeek(ev.start_date.substring(0, 10)),
                            f_start_date: this.formattedTime(ev.start_date),
                            f_end_date: this.formattedTime(this.addDurationToTime(ev.start_date.slice(-8), ev.length))

                        };
                    })
                };
            })
        },
        async getEventByWeek() {

            const eventsForWeek = {};
            await this.daysOfWeek
            for (const [index, day] of this.days.entries()) {
                const day_nb = this.daysOfWeek[index];
                eventsForWeek[day] = {
                    day: day,
                    calendar: "0",
                    calendar_color: " ",
                    day_nb: day_nb,
                    frequence: " ",
                    color: " ",
                    events: []
                };
            }

            this.Calendar.forEach((calendar) => {
                calendar.event.forEach((event) => {
                    if (event.week == this.selectedWeek) {
                        console.log(calendar.calendar_color)
                        const day = event.day;
                        const id_cal = calendar.id_calendar
                        const day_nb = event.day_nb;
                        const color = event.color;
                        eventsForWeek[day].calendar_color = calendar.calendar_color;
                        eventsForWeek[day].frequence = event.to_repeat,
                            eventsForWeek[day].color = color;
                        eventsForWeek[day].id_cal = id_cal;
                        eventsForWeek[day].day_nb = day_nb;
                        eventsForWeek[day].events.push({ event: event });
                    }
                });
            });

            this.EventByWeek = eventsForWeek;
            return eventsForWeek;
        },
        calculateDuration(startTime, endTime) {
            const [startHours, startMinutes] = startTime.split(':').map(Number);
            const [endHours, endMinutes] = endTime.split(':').map(Number);

            const startInMinutes = startHours * 60 + startMinutes;
            const endInMinutes = endHours * 60 + endMinutes;

            const durationInMinutes = endInMinutes - startInMinutes;

            return durationInMinutes;
        },
        AddEvent() {
            if (this.SelectedCalendar === '0' || this.SelectedDate === '' || this.SelectedType === '0' || this.SelectedFrequence === 'first'
                || this.StartTime === '0' || this.EndTime === '0' || this.SelectedEventName === '') {
                this.message = 'You must fill all the required fields';
                console.log(this.SelectedCalendar, this.SelectedDate, this.SelectedType, this.SelectedFrequence, this.StartTime, this.EndTime, this.SelectedEventName);
            } else if (this.StartTime > this.EndTime) {
                this.message = 'Dates are not valid';
            } else {
                const token = localStorage.getItem('token');
                const date = new Date(this.SelectedDate + ' ' + this.StartTime);
                const start_date = `${date.toLocaleDateString('fr-FR', { day: '2-digit', month: '2-digit', year: 'numeric' }).replace(/\//g, '-')} ${date.toLocaleTimeString('fr-FR', { hour12: false })}`;
                fetch('api/api/events', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    },
                    body: JSON.stringify({ name_event: this.SelectedEventName, description: 'Description', start_date: start_date, length: this.calculateDuration(this.StartTime, this.EndTime), priority_level: this.SelectedImportance, to_repeat: this.SelectedFrequence, movable: true, color: this.SelectedType, id_calendar: this.SelectedCalendar })
                })
                    .then((response) => {
                        console.log(response.json());
                        if (response.ok) {
                            this.message = '';
                            // this.Reload();
                            return response.json();
                        } else {
                            return response.json().then(error => {
                                throw new Error(JSON.stringify(error));
                            });
                        }
                    })
                    .then((eventData) => {
                        // Event created successfully, now create the tasks
                        const List = [];
                        if (this.taskInput !== '') {
                            if (this.taskChecked !== true) {
                                this.taskChecked = false;
                            }
                            List.push({
                                name_task: this.taskInput,
                                description: 'description',
                                priority_level: this.selectedImportance,
                                is_done: this.taskChecked,
                            });
                        }

                        this.AddTasks.forEach((new_task, index) => {
                            const checkboxElement = document.getElementById('taskChecked_' + index);
                            const inputElement = this.taskInputArray[index];
                            const importanceElement = this.selectedImportanceArray[index];
                            const checkedState = checkboxElement.checked;
                            if (inputElement !== '') {
                                List.push({
                                    name_task: inputElement,
                                    description: 'description',
                                    priority_level: importanceElement,
                                    is_done: checkedState,
                                });
                            }
                        });

                        const createTaskPromises = List.map((task) => {
                            return fetch('api/api/atasks', {
                                method: 'POST',
                                headers: {
                                    'Content-Type': 'application/json',
                                    Authorization: 'Bearer ' + token,
                                },
                                body: JSON.stringify({name_task: task.name_task, description: 'Description', priority_level: task.priority_level, is_done: task.is_done, id_event : eventData.id_event}),
                            });
                        });

                        Promise.all(createTaskPromises)
                            .then((taskResponses) => {
                            
                                console.log(taskResponses);
                                this.message = '';
                                this.SelectedType = '0';
                                this.SelectedFrequence = 'first';
                                this.SelectedEventName = ' ';
                                this.SelectedDay = '0';
                                this.StartTime = '0';
                                this.SelectedDate = '0';
                                this.EndTime = '0';
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
        UpdateEvent() {

            if (this.SelectedDate == "" || this.SelectedType == "0" || this.SelectedFrequence == "first" || this.StartTime == "0" || this.EndTime == "0" || this.SelectedEventName == "") {
                this.message = 'You must fill all the required fields'

            } else if (this.StartTime > this.EndTime) {
                this.message = 'Dates are not valid'
            } else {
                const token = localStorage.getItem('token');
                const date = new Date(this.SelectedDate + " " + this.StartTime)
                const start_date = `${date.toLocaleDateString('fr-FR', { day: '2-digit', month: '2-digit', year: 'numeric' }).replace(/\//g, '-')} ${date.toLocaleTimeString('fr-FR', { hour12: false })}`;
                fetch("api/api/events/" + this.SelectedEvent,
                    {
                        method: 'PATCH',
                        headers: {
                            'Content-Type': 'application/json',
                            'Authorization': 'Bearer ' + token
                        },
                        body: JSON.stringify({ name_event: this.SelectedEventName, description: "Description", start_date: start_date, length: this.calculateDuration(this.StartTime, this.EndTime), priority_level: this.SelectedImportance, to_repeat: this.SelectedFrequence, movable: true, color: this.SelectedType, id_calendar: this.SelectedCalendar })
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

            }
        },
        OpenDeleteEvent() {
            document.getElementById("myEventDelete").style.display = "block";
        },
        CloseDeleteEvent() {
            document.getElementById("myEventDelete").style.display = "none";
        },
        DeleteEvent() {

            const token = localStorage.getItem('token');

            fetch("api/api/events/" + this.SelectedEvent,
                {
                    method: 'DELETE',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + token
                    },
                })
                .then((response) => {
                    if (response.ok) {
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
            this.SelectedCalendar = "0";
            this.SelectedEvent = "";
            this.Reload();
        },
        handleBeforeUnload() {

            const currentWeek = new Date().toISOString().slice(0, 10)
            localStorage.setItem("selectedWeek", this.getWeek(currentWeek));
        },
        Reload() {
            window.location.reload();
            localStorage.setItem("selectedWeek", this.selectedWeek);
        }

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
    beforeMount() {
        this.initializePage().then(() => {
            this.getEventByWeek(this.selectedWeek);
            this.visibleCalendars = this.Calendar.map((calendar) => calendar.id_calendar);
            console.log(this.Calendar)

        });
    },
    beforeUnmount() {
        window.removeEventListener("beforeunload", this.handleBeforeUnload);
    }
};

/*
window.onload = function () {



     Get the modal2
    var modal2 = document.getElementById("NewCalendarModal");

     Get the button that opens the modal
    var btn2 = document.getElementById("addCalendar");

     Get the <span> element that closes the modal
    var span2 = document.getElementsByClassName("close")[0];

     When the user clicks the button, open the modal
    if (btn2) {
        btn2.onclick = function () {
            modal2.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span2) {
         When the user clicks on <span> (x), close the modal
        span2.onclick = function () {
            modal2.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
     When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal2) {
            modal2.style.display = "none";
        }
    };

     Get the modal3
    var modal3 = document.getElementById("LoadCalendarModal");

     Get the button that opens the modal
    var btn3 = document.getElementById("event");

     Get the <span> element that closes the modal
    var span3 = document.getElementsByClassName("close")[1];

     When the user clicks the button, open the modal
    if (btn3) {
        btn3.onclick = function () {
            modal2.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span3) {
         When the user clicks on <span> (x), close the modal
        span3.onclick = function () {
            modal3.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
     When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal3) {
            modal3.style.display = "none";
        }
    };



     Get the modal2
    var modal4 = document.getElementById("myModalNewCalendar");

     Get the button that opens the modal
    var btn4 = document.getElementById("AddCalendar");

     Get the <span> element that closes the modal
    var span4 = document.getElementsByClassName("close")[3];

     When the user clicks the button, open the modal
    if (btn4) {
        btn4.onclick = function () {
            modal4.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span4) {
         When the user clicks on <span> (x), close the modal
        span4.onclick = function () {
            modal4.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
     When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal4) {
            modal4.style.display = "none";
        }
    };


     Get the modal3
    var modal5 = document.getElementById("ImportCalendarModal");

     Get the button that opens the modal
    var btn5 = document.getElementById("import-pop-up");

     Get the <span> element that closes the modal
    var span5 = document.getElementsByClassName("close")[2];

     When the user clicks the button, open the modal
    if (btn5) {
        btn5.onclick = function () {
            modal5.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span5) {
         When the user clicks on <span> (x), close the modal
        span5.onclick = function () {
            modal5.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
     When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal5) {
            modal5.style.display = "none";
        }
    };

    modal 6

    var modal6 = document.getElementsByClassName("event");

     Get the button that opens the modal
    var btn6 = document.getElementById("blankCalendar");

    if (btn6) {
        btn6.onclick = function () {
            modal6.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
*/
    //dropdown list

    //var x, i, j, l, ll, selElmnt, a, b, c;
/*look for any elements with the class "custom-select":*/
/*  x = document.getElementsByClassName("custom-select");
  l = x.length;
  for (i = 0; i < l; i++) {
      selElmnt = x[i].getElementsByTagName("select")[0];
      ll = selElmnt.length;
      
      a = document.createElement("DIV");
      a.setAttribute("class", "select-selected");
      a.innerHTML = selElmnt.options[selElmnt.selectedIndex].innerHTML;
      x[i].appendChild(a);
    
      b = document.createElement("DIV");
      b.setAttribute("class", "select-items select-hide");
      for (j = 1; j < ll; j++) {
          /*for each option in the original select element,
            
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



};*/
</script>

<style></style>
