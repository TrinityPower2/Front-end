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
                    <router-link to="/todo-list-page" class="to-page-nav">My Plannings</router-link>
                    <router-link to="/todo-list-page" class="to-page-nav">My Todo Lists</router-link>
                    <router-link to="/todo-list-page" class="to-page-nav">Create a Planning</router-link>
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
                <div class="Todolists-disp">
                    <div class="high-part-todo">
                        <div></div>
                        <h1 class="Todo-title">My Todo Lists</h1>
                        <font-awesome-icon id="AddList" icon="fa-solid fa-plus" size="2xl" class="Plus-todo" />
                    </div>
                    <div class="Todolist-shape">
                        <div class="TodoList">
                            <div class="List-Title">Due Today</div>
                            <div class="Task">
                                <label for="scales" class="task-container">Finish this page
                                    <input type="checkbox" id="scales" name="test1" checked="checked" />
                                    <span class="checkmark"></span>
                                </label>
                                <font-awesome-icon id="TaskPlus" icon="fa-solid fa-plus" size="s" />
                            </div>
                            <div class="Task">
                                <label class="task-container">Buy food for party
                                    <input type="checkbox" />
                                    <span class="checkmark"></span>
                                </label>
                                <font-awesome-icon icon="fa-solid fa-plus" size="s" />
                            </div>
                            <div class="Task">
                                <label class="task-container">Upload finished work on Github with the bros
                                    <input type="checkbox" />
                                    <span class="checkmark"></span>
                                </label>
                                <font-awesome-icon icon="fa-solid fa-plus" size="s" />
                            </div>

                            <button type="submit" class="Task-add-btn" id="addBtn">
                                Add Task
                            </button>
                        </div>
                        <div class="TodoList"></div>
                        <div class="TodoList"></div>
                        <div class="TodoList"></div>
                    </div>
                </div>
                <!-- The Modal -->
                <div id="myModal" class="modal">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span class="close">&times;</span>
                        <h1 class="modal-Title">Due Today</h1>
                        <div class="modal-center">
                            <div class="AddInputBox">
                                <input type="text" placeholder="Name Task" name="email" />
                            </div>
                            <div class="custom-select">
                                <select>
                                    <option value="0">Importance :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                            </div>
                            <div class="AddInputBox">
                                <input type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>

                <div id="myModalPlus" class="modal">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span class="close">&times;</span>
                        <h1 class="modal-Title">Add to Planner</h1>
                        <div class="modal-center">
                            <div class="custom-select">
                                <select>
                                    <option value="0">Add to Task :</option>
                                    <option value="1">Urgent</option>
                                    <option value="2">Important</option>
                                    <option value="3">Medium</option>
                                    <option value="4">Minor</option>
                                    <option value="5">Do Later</option>
                                </select>
                            </div>
                            <div class="AddInputBox">
                                <input type="submit" value="Add" name="submit" />
                            </div>
                        </div>
                    </div>
                </div>


                <div id="NewListModal" class="modal1">
                    <!-- Modal content -->
                    <div class="modal-content">
                        <span class="close">&times;</span>
                        <h1 class="modal-Title" style="margin-bottom : 40px;">New Todo List</h1>
                        <div class="modal-center1">
                            <div class="New-list-element">
                                <div class="new-list-desc">
                                    Day
                                </div>
                                <div class="custom-select">
                                    <select>
                                        <option value="0">Choose day :</option>
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
                                <div class="new-list-desc" >
                                    Tasks
                                </div>
                                <div class="Add-another-task">
                                    <div class="new-task-create">
                                        <label class="task-container" style="margin-left: 0%;">
                                            <input type="checkbox" />
                                            <span class="checkmark"></span>
                                        </label>
                                        <input type="text" id="fname" name="fname" class="new-task-input" placeholder="..."><br>
                                    </div>
                                    <div class="new-task-create" style="margin-top:8px;">
                                        <label class="task-container" style="margin-left: 0%;">
                                            <input type="checkbox" />
                                            <span class="checkmark"></span>
                                        </label>
                                        <input type="text" id="fname" name="fname" class="new-task-input" placeholder="..."><br>
                                    </div>
                                    <div class="new-task-create">
                                        <font-awesome-icon icon="fa-solid fa-plus" size="s" />
                                        <p>New Task</p>
                                    </div>
                                </div>
                            </div>
                            <div class="New-list-element">
                                <div class="new-list-desc">
                                    Add to planner
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
                            <div style="width:65%; display:flex; justify-content:center; margin-top: 50px;">
                            <div class="AddTaskInputBox">
                                <input type="submit" value="Add" name="submit" />
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
    name: "TodoListPage",
    components: {
        DarkLightMode,
    },
};
window.onload = function () {
    // Get the modal
    var modal = document.getElementById("myModal");

    // Get the button that opens the modal
    var btn = document.getElementById("addBtn");

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

    //dropdown list

    var x, i, j, l, ll, selElmnt, a, b, c;
    /*look for any elements with the class "custom-select":*/
    x = document.getElementsByClassName("custom-select");
    l = x.length;
    for (i = 0; i < l; i++) {
        selElmnt = x[i].getElementsByTagName("select")[0];
        ll = selElmnt.length;
        /*for each element, create a new DIV that will act as the selected item:*/
        a = document.createElement("DIV");
        a.setAttribute("class", "select-selected");
        a.innerHTML = selElmnt.options[selElmnt.selectedIndex].innerHTML;
        x[i].appendChild(a);
        /*for each element, create a new DIV that will contain the option list:*/
        b = document.createElement("DIV");
        b.setAttribute("class", "select-items select-hide");
        for (j = 1; j < ll; j++) {
            /*for each option in the original select element,
                  create a new DIV that will act as an option item:*/
            c = document.createElement("DIV");
            c.innerHTML = selElmnt.options[j].innerHTML;
            c.addEventListener("click", function () {
                /*when an item is clicked, update the original select box,
                        and the selected item:*/
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
                  and open/close the current select box:*/
            e.stopPropagation();
            closeAllSelect(this);
            this.nextSibling.classList.toggle("select-hide");
            this.classList.toggle("select-arrow-active");
        });
    }
    function closeAllSelect(elmnt) {
        /*a function that will close all select boxes in the document,
            except the current select box:*/
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
      then close all select boxes:*/
    document.addEventListener("click", closeAllSelect);



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
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal1) {
            modal1.style.display = "none";
        }
    };




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
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function (event) {
        if (event.target == modal2) {
            modal2.style.display = "none";
        }
    };
};
</script>

<style></style>
