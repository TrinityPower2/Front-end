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
                <button class="Your-calendar-button">
                    <p class="your-calendar-letter">P</p>
                </button>
                <div class="Add-calendar-sidebar" @click = "OpenmyModalNewCalendar"><font-awesome-icon id="AddCalendar" icon="fa-solid fa-plus" size="lg"
                        style="color:rgba(47, 43, 44, 0.648)" />
                </div>
            </div>
            <div class="calendar-display-container">
                <div class="calendar-top-buttons">
                    <div class="choose-week">
                        <div>
                            <input id="party" type="week" name="partydate" class="Create-planning-Btn">
                        </div>
                        <font-awesome-icon icon="fa-solid fa-angle-left" class="arrow-left-calendar" />
                        <font-awesome-icon icon="fa-solid fa-angle-right" class="arrow-left-calendar" />
                    </div>
                    <button class="Create-planning-Btn" id="addCalendar" @click = "OpenNewCalendar">
                        Add Event
                    </button>
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
                            <div class="day mon">
                                <div class="date">
                                    <p class="date-num">9</p>
                                    <p class="date-day">Mon</p>
                                </div>
                                <div class="events">
                                    <div class="event start-13 end-15 project calendar-2">
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
                                    <div class="event start-16 end-18-30 health calendar-1" id="event">
                                        <p class="calendar-title">Volleyball Practice</p>
                                        <p class="calendar-time">16H - 18H30</p>
                                    </div>
                                    <div class="event start-10 end-11-30 class calendar-8" @click = "OpenLoadCalendarModal">
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
                                    <div class="event start-12 end-19 holiday calendar-4">
                                        <p class="calendar-title">Dentist Apointment</p>
                                        <p class="calendar-time">12H - 19H</p>
                                    </div>
                                    <div class="event start-8 end-9-30 project calendar-6">
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
                                    <div class="event start-10 end-12 health calendar-4">
                                        <p class="calendar-title">Volleyball Practice</p>
                                        <p class="calendar-time">10H - 12H</p>
                                    </div>
                                    <div class="event start-19 end-23 party calendar-5">
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
                                    <div class="event start-11 end-16 work calendar-7">
                                        <p class="calendar-title">Volleyball Practice</p>
                                        <p class="calendar-time">11H - 16H</p>
                                    </div>
                                    <div class="event start-15 end-20 family calendar-2">
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
                                    <div class="event start-11 end-15 holiday calendar-1">
                                        <p class="calendar-title">Flight to Dubai</p>
                                        <p class="calendar-time">11H - 15H</p>
                                    </div>
                                    <div class="event start-7 end-9 project calendar-3">
                                        <p class="calendar-title">English Exam</p>
                                        <p class="calendar-time">7H - 9H</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="NewCalendarModal" class="modal1">
                <div class="modal-content-create" style="max-width:800px;">
                    <span class="close" @click = "CloseNewCalendar">&times;</span>
                    <h1 class="modal-Title" style="margin-bottom: 40px">New Event</h1>
                    <div class="modal-center1">
                        <input type="text" id="fname" name="fname" class="new-task-input" placeholder="Event Name" /><br />
                        <div class="New-list-element1" style="margin-top: 40px">
                            <!-- <div class="new-list-desc">
                                    Day
                                </div> -->
                            <font-awesome-icon icon="fa-regular fa-clock" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Type of event :</option>
                                    <option value="1">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #00ff88" />
                                        Party
                                    </option>
                                    <option value="2">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff" />
                                        Project
                                    </option>
                                    <option value="3">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #d400ff" />
                                        Work
                                    </option>
                                    <option value="4">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae" />
                                        Health
                                    </option>
                                    <option value="5">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033" />
                                        Holiday
                                    </option>
                                    <option value="6">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff8800" />
                                        Family
                                    </option>
                                    <option value="7">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffdd00" />
                                        Class
                                    </option>
                                    <option value="8">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffffff" />
                                        Custom
                                    </option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-repeat" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
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
                        <div class="New-list-element" style="margin-left: 14%">
                            <font-awesome-icon icon="fa-solid fa-list-check" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                    <font-awesome-icon icon="fa-solid fa-plus" size="s" />
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
                                <input type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="LoadCalendarModal" class="modal1">
                <div class="modal-content-create" style="max-width:800px;">
                    <span class="close" @click = "CloseLoadCalendarModal" >&times;</span>
                    <h1 class="modal-Title" style="margin-bottom: 40px">Edit Event</h1>
                    <div class="modal-center1">
                        <input type="text" id="fname" name="fname" class="new-task-input" placeholder="Event Name" /><br />
                        <div class="New-list-element1" style="margin-top: 40px">
                            <!-- <div class="new-list-desc">
                                    Day
                                </div> -->
                            <font-awesome-icon icon="fa-regular fa-clock" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                style="color: rgba(85, 84, 85, 0.986)" />
                            <div class="custom-select create-select">
                                <select>
                                    <option value="0">Type of event :</option>
                                    <option value="1">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #00ff88" />
                                        Party
                                    </option>
                                    <option value="2">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff" />
                                        Project
                                    </option>
                                    <option value="3">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #d400ff" />
                                        Work
                                    </option>
                                    <option value="4">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae" />
                                        Health
                                    </option>
                                    <option value="5">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033" />
                                        Holiday
                                    </option>
                                    <option value="6">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ff8800" />
                                        Family
                                    </option>
                                    <option value="7">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffdd00" />
                                        Class
                                    </option>
                                    <option value="8">
                                        <font-awesome-icon icon="fa-solid fa-circle" style="color: #ffffff" />
                                        Custom
                                    </option>
                                </select>
                            </div>
                        </div>
                        <div class="New-list-element1">
                            <font-awesome-icon icon="fa-solid fa-repeat" size="xl" style="color: rgba(85, 84, 85, 0.986)" />
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
                        <div class="New-list-element" style="margin-left: 14%">
                            <font-awesome-icon icon="fa-solid fa-list-check" size="xl"
                                style="color: rgba(85, 84, 85, 0.986)" />
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
                                    <font-awesome-icon icon="fa-solid fa-plus" size="s" />
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
                                <input type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="myModalNewCalendar" class="modal">
                <!-- Modal content -->
                <div class="modal-content">
                    <span class="close" @click = "ClosemyModalNewCalendar">&times;</span>
                    <h1 class="modal-Title">Add New Calendar</h1>
                    <div class="modal-center">
                        <p style="margin-top: 50px;">How would you like to create you new calendar ?</p>
                        <div class="delete-list-button">
                            <div class="AddTaskInputBox no">
                                <input class="close" type="submit" @click = "OpenImportCalendarModal" value="Import Calendar" name="submit"
                                    id="import-pop-up" />
                            </div>
                            <div class="AddTaskInputBox no">
                                <div class="pop-up-route-container">
                                    <router-link class="pop-up-route" to="/create-calendar-page">New Optimized
                                        Calendar</router-link>
                                </div>
                                <!-- <input class="close" type="submit" value="New Optimized Calendar" name="submit" /> -->
                            </div>
                            <div class="AddTaskInputBox no">
                                <input style="margin-left: 0px;" type="submit" value="New Blank Calendar" name="submit"
                                    id="blankCalendar" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="ImportCalendarModal" class="modal1">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close" @click = "CloseImportCalendarModal">&times;</span>
                <h1 class="modal-Title" style="margin-bottom : 40px;" >Import Planning</h1>
                <div class="modal-center2">
                    <div class="New-list-element">
                        <div class="new-list-desc">
                            ICAL Link
                        </div>
                        <input type="text" id="fname" name="fname" class="new-task-input" style="width:50%"
                            placeholder="..."><br>
                    </div>
                    <div class="New-list-element">
                        <div class="new-list-desc">
                            Colors
                        </div>
                        <div class="custom-select">
                            <select>
                                <option value="0">Choose a Color :</option>
                                <option value="1"><font-awesome-icon icon="fa-solid fa-circle" style="color: #00ff88;" />
                                    Green</option>
                                <option value="2"><font-awesome-icon icon="fa-solid fa-circle" style="color: #0084ff;" />
                                    Blue</option>
                                <option value="3"><font-awesome-icon icon="fa-solid fa-circle" style="color: #d400ff;" />
                                    Purple</option>
                                <option value="4"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff00ae;" />
                                    Pink</option>
                                <option value="5"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff0033;" />
                                    Red</option>
                                <option value="6"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ff8800;" />
                                    Orange</option>
                                <option value="7"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ffdd00;" />
                                    Yellow</option>
                                <option value="8"><font-awesome-icon icon="fa-solid fa-circle" style="color: #ffffff;" />
                                    Custom</option>
                            </select>
                        </div>
                    </div>

                    <div style="width:50%; display:flex; justify-content:center; margin-top: 50px;">
                        <div class="AddTaskInputBox">
                            <input type="submit" value="Add" name="submit" />
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="myTaskDelete" class="modal">
            <!-- Modal content -->
            <div class="modal-content">
                <span class="close">&times;</span>
                <h1 class="modal-Title">Delete Task</h1>
                <div class="modal-center">
                    <p style="margin-top: 50px;">Are you sure you want to delete this Task ?</p>
                    <div class="delete-list-button">
                        <div class="AddTaskInputBox no">
                            <input class="close" type="submit" value="Cancel" name="submit" />
                        </div>
                        <div class="AddTaskInputBox no">
                            <input style="margin-left: 0px;" type="submit" value="Delete" name="submit" />
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
    name: "CalendarPage",
    components: {
        DarkLightMode,
        UserMenu,
    },
    methods : {
        OpenNewCalendar(){
            document.getElementById("NewCalendarModal").style.display = "block";
        },
        CloseNewCalendar(){
            document.getElementById("NewCalendarModal").style.display = "none";
        },
        OpenLoadCalendarModal(){
            document.getElementById("LoadCalendarModal").style.display = "block";
        },
        CloseLoadCalendarModal(){
            document.getElementById("LoadCalendarModal").style.display = "none";
        },
        OpenmyModalNewCalendar(){
            document.getElementById("myModalNewCalendar").style.display = "block";
        }, 
        ClosemyModalNewCalendar(){
            document.getElementById("myModalNewCalendar").style.display = "none";
        },
        OpenImportCalendarModal(){
            document.getElementById("ImportCalendarModal").style.display = "block";
        },
        CloseImportCalendarModal(){
            document.getElementById("ImportCalendarModal").style.display = "none";
        },
        OpenEvent(){
            document.getElementById("event").style.display = "block";
        },
        CloseEvent(){
            document.getElementById("event").style.display = "none";
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
    },
};

/*
window.onload = function () {



    // Get the modal2
    var modal2 = document.getElementById("NewCalendarModal");

    // Get the button that opens the modal
    var btn2 = document.getElementById("addCalendar");

    // Get the <span> element that closes the modal
    var span2 = document.getElementsByClassName("close")[0];

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
    var modal3 = document.getElementById("LoadCalendarModal");

    // Get the button that opens the modal
    var btn3 = document.getElementById("event");

    // Get the <span> element that closes the modal
    var span3 = document.getElementsByClassName("close")[1];

    // When the user clicks the button, open the modal
    if (btn3) {
        btn3.onclick = function () {
            modal2.style.display = "block";
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
    var modal4 = document.getElementById("myModalNewCalendar");

    // Get the button that opens the modal
    var btn4 = document.getElementById("AddCalendar");

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


    // Get the modal3
    var modal5 = document.getElementById("ImportCalendarModal");

    // Get the button that opens the modal
    var btn5 = document.getElementById("import-pop-up");

    // Get the <span> element that closes the modal
    var span5 = document.getElementsByClassName("close")[2];

    // When the user clicks the button, open the modal
    if (btn5) {
        btn5.onclick = function () {
            modal5.style.display = "block";
        };
    } else {
        console.log("element not found");
    }
    if (span5) {
        // When the user clicks on <span> (x), close the modal
        span5.onclick = function () {
            modal5.style.display = "none";
        };
    } else {
        console.log("element not found");
    }
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal5) {
            modal5.style.display = "none";
        }
    };

    //modal 6

    var modal6 = document.getElementsByClassName("event");

    // Get the button that opens the modal
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

//    var x, i, j, l, ll, selElmnt, a, b, c;
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
