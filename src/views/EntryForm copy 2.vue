<template>
    <body>
        <a id="top"></a>
        <!-- <?php if($_SESSION['admin']==1){?> -->
        <div class="FormPage1">
            <div class="headernav" >
                <div class="header-container1">
            <div class="header-image">
                <img alt="Vue logo" style="opacity: 0.7;" src="../assets/TimeToDo1.png" class="VueLogo" />
            </div>
            <div class="Navbar">
                    <router-link to="/todo-list-page" class="to-page-nav">My Plannings</router-link>
                    <router-link to="/todo-list-page" class="to-page-nav">My Todo Lists</router-link>
                    <router-link to="/create-calendar-page" class="to-page-nav">Create a Planning</router-link>
                </div>
                <UserMenu></UserMenu>
                </div>
            </div>
            <div class="FormBox">
                <div class="FormContainer">
                    <div class="Form-banner-container">
                        <div class="loginForm">
                            <h2>Your Preferences</h2>
                            <p class="Form-presentation"> <br> TimeToDo depends on an <i class="fa fa-bold" aria-hidden="true">algorithm</i>  to optimize your plannings. <br><br> The following questions will help us <i class="fa fa-bold" aria-hidden="true">taylor your planning</i> , depending on your needs :<br><br></p>
                            <form action="#" method="post">
                                <p class="Form-question">On which timeslot is your lunch break ?</p>
                                <input type="hidden" name="nbquestion" style="display: none"
                                    value="<?php echo $row['nbquestion']; ?>" />
                                
                                    <input type="hidden" name="question" style="display: none"
                                    value="<?php echo $row['question']; ?>" />
                                <input type="hidden" name="answer" style="display: none"
                                    value="<?php echo $row['answer']; ?>" />
                                <input type="hidden" name="category" style="display: none"
                                    value="<?php echo $row['category']?>" />
                                <input type="hidden" name="level" style="display: none"
                                    value="<?php echo $row['level']?>" />
                                <div class="loginInputBox">
                                    <input type="time" step="900" name="txtQuestion" style="width:50%;"/>
                                    <input type="time" step="900" name="txtQuestion" style="width:50%"/>
                                </div>
                                <p class="Form-question">On which timeslot is your diner break ?</p>
                                <div class="loginInputBox">
                                    <input type="time" step="900" name="txtQuestion" style="width:50%"/>
                                    <input type="time" step="900" name="txtQuestion" style="width:50%"/>
                                </div>
                                <p class="Form-question">What is your sleeping schedule ?</p>
                                <div class="loginInputBox">
                                    <input type="time" step="900" name="txtQuestion" style="width:50%"/>
                                    <input type="time" step="900" name="txtQuestion" style="width:50%"/>
                                </div>
                                <p class="Form-question">Would you rather have schedules in the morning or the afternoon ?</p>
                                <div class="Switch-container">
                                    <p class="Switch-label">Morning</p>
                                    <label class="switch">
                                        <input type="checkbox">
                                        <span class="slider"></span>
                                    </label>
                                    <p class="Switch-label">Afternoon</p>
                                </div>
                                <!-- <div class="loginInputBox">
                                    <input type="text" name="txtCategory" value="<?php echo $row['category']?>" />
                                </div>
                                <div class="loginInputBox">
                                    <input type="text" name="txtLevel" value="<?php echo $row['level']?>" />
                                </div> -->
                                <br><br>
                                <div class="loginInputBox FormInputBox">
                                    <input type="submit" value="Submit Information" name="btnUpdate" />
                                </div>
                                <p class="forgotPswd MoveOn">
                                    Skip for now ?<a href="./Register.html">Move on</a>
                                </p>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"><font-awesome-icon icon="fa-solid fa-arrow-up" size="xs" style="color: #fff0fe;" /></a>
        <footer style="margin-top: 0%">
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
// import DarkLightMode from "../components/DarkLightMode.vue";
export default {
    name: "EntryFormPage2",
    components: {
    UserMenu,
    // DarkLightMode
    },
    mounted(){
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
    }
};
</script>

<style></style>
<!-- <?php }else{?> 
            <section class="LoginPage">
            <div class="TestColor" style="--color:rgb(11, 88, 241);"></div>
            <div class="TestColor" style="--color:rgb(137, 137, 251);"></div>
            <div class="TestColor" style="--color:rgb(144, 237, 242);"></div>
                <div class="loginBox">
                    <div class="loginSquares" style="--i:0;"></div>
                    <div class="loginSquares" style="--i:1;"></div>
                    <div class="loginSquares" style="--i:2;"></div>
                    <div class="loginSquares" style="--i:3;"></div>
                    <div class="loginSquares" style="--i:4;"></div>
                    <div class="loginContainer">
                        <div class="loginForm">
                            <h2>Edit Category</h2>
                            <form action="#" method="post">
                                <br>
                                <br>
                                <h1>This is an Admin-Only page</h1>
                                <br>
                                <br>
                                <br>
                                <br>
                                <p class="forgotPswd">Got lost on the way ?<a href="./.html" style="color:rgb(133, 45, 247)">Go back home</a></p>
                            </form>
                        </div>
                    </div>
                </div>
            </section>
    <?php } ?> -->
