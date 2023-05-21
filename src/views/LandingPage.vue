<template>
    <body>
        <div class="Landing-page-container">
        <header>
            <div class="header-container">
                <div class="header-image">
                    <img alt="Vue logo" src="../assets/TimeToDo1.png" class="VueLogo" />
                </div>
                <div>
                    <router-link to="/login-page" class="LogRegBtnLink"
                        style="--shadow: #16dcff; --color: #f291bb; --background: #f291bbba">Login</router-link>
                    <router-link to="/register-page" class="LogRegBtnLink"
                        style="--shadow: #f291bb; --color: #16dcff; --background: #16dcffab">Register</router-link>
                </div>
            </div>
        </header>

        <a id="top"></a>
        <div class="WelcomePrompt">
            <div class="Landing-banner-container">
                <div class="Landing-banner">
                    <div class="Landing-banner-text">
                        <h2 class="Slogan">Take control of your time</h2>
                        <br />
                        <h2 class="TimeToDo">Time To Do</h2>
                        <br />
                        <h2 class="Slogan">An interactive planner</h2>
                    </div>
                    <div>
                        <img src="../assets/LangingPage.png" alt="Landing-png" class="Landing-png" />
                    </div>
                </div>
            </div>
            <p>
                Always wanted to organize yourself, but never found the right tool to do
                so?<br /><br />This is the place for you
            </p>

            <a href="./Register.html" class="TryOutBtnLink">Try it out!</a>
        </div>
        <div class="SiteContent-container">
            <div class="VocabPrez">
                <div class="VocabDescription">
                    <h1 class="VocabH1">Create colorful calendars</h1>
                    <p>
                        Never lose track of your events!
                        <br /><br />
                        With Time To Do, you can easily create and update dynamically your calendars.
                    </p>
                </div>
                <img src="../assets/PlannerLanding.jpg" alt="Planner demo" class="Vocabdemo">
            </div>
            <div class="ExoPrez">
                <img src="../assets/AddTaskLanding.jpg" alt="Add Task demo" class="Vocabdemo">
                <div class="ExoDescription">
                    <h1>Personalize your events</h1>
                    <p>
                        Each event can be customized, by setting the importance, if it needs to be
                        repeated, ...  <br /><br />
                        You can even include sub-tasks in your event for a more detailed approach of 
                        your organization.
                    </p>
                </div>
            </div>
            <div class="VocabPrez">
                <div class="VocabDescription">
                    <h1 class="TestH1">Try out our Time To Do lists</h1>
                    <p>
                        Not a fan of calendars? Don't worry, you can also create and personalize 
                        your own to-do lists.<br /><br />
                        You won't ever forget to call your mom!
                    </p>
                </div>
                <img src="../assets/ToDoLanding.jpg" alt="ToDo demo" class="Vocabdemo">
            </div>
            <div class="WelcomePrompt WelcomeEnd">
                <h1> </h1>
                <a href="./Register.html" class="TryOutBtnLink">Get started!</a>
            </div>
        </div>
        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"><font-awesome-icon icon="fa-solid fa-arrow-up" size="xs" style="color: #fff0fe;" /></a>
        <footer>
            <div class="content-footer">
                <div class="top">
                    <div class="logo-details">
                        <img src="../assets/TimeToDo1.png" alt="LB logo">
                        <p class="logo-name">
                            TIME TO DO <br />
                            <small>est. 2023</small>
                        </p>
                    </div>
                    <div class="media-icons">
                        <a href="https://www.linkedin.com/in/lou-brunesseaux-a843aa248"><font-awesome-icon icon="fa-brands fa-linkedin-in"/></a>
                        <a href="mailto:loubruness@gmail.com"><font-awesome-icon icon="fa-brands fa-google" /></a>
                        <a href="https://github.com/loubruness"><font-awesome-icon icon="fa-brands fa-github"/></a>
                    </div>
                </div>
            </div>
        </footer>
    </div>
    </body>
</template>

<script>
export default {
    name: "LandingPage",
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

<style>

</style>
