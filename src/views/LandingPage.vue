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
                so ?<br /><br />This is the place for you
            </p>

            <a href="./Register.html" class="TryOutBtnLink">Try it out !</a>
        </div>
        <div class="SiteContent-container">
            <div class="VocabPrez">
                <div class="VocabDescription">
                    <h1 class="VocabH1">Learn 350+ new words</h1>
                    <p>
                        Enrich your vocabulary with our 12, level-based, word categories.
                        <br /><br />
                        Learn how to address people, differenciate colors and discuss the
                        weather !
                    </p>
                </div>
                <img src="../assets/PlannerLanding.jpg" alt="Planner demo" class="Vocabdemo">
            </div>
            <div class="ExoPrez">
                <img src="../assets/AddTaskLanding.jpg" alt="Add Task demo" class="Vocabdemo">
                <div class="ExoDescription">
                    <h1>Practise your proficiency</h1>
                    <p>
                        Each category provides you with Exercises to test how well you've
                        integrated the new vocabulary. <br /><br />
                        These exercises are dependant on your level (Beginner,Intermediate
                        or Expert) and adaptable to your personnal profile.
                    </p>
                </div>
            </div>
            <div class="VocabPrez">
                <div class="VocabDescription">
                    <h1 class="TestH1">Evaluate your progress</h1>
                    <p>
                        Tests, for each level of each category, are put at your disposal to
                        evaluate your mastery of the topics. <br /><br />
                        Fluency is only a couple of tests away!
                    </p>
                </div>
                <img src="../assets/ToDoLanding.jpg" alt="ToDo demo" class="Vocabdemo">
            </div>
            <div class="WelcomePrompt WelcomeEnd">
                <h1> </h1>
                <a href="./Register.html" class="TryOutBtnLink">Get started !</a>
            </div>
        </div>
        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"></a>
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
};
</script>

<style>

</style>
