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
                    <router-link to="/create-calendar-page" class="to-page-nav">Create a Planning</router-link>
                </div>
                <UserMenu></UserMenu>
                <div class="light">
                    <DarkLightMode></DarkLightMode>
                </div>
            </div>
        </header>
        <a id="top"></a>
        <div class="help-page">
            <div class="help-page-container">
                <h1 class="modal-Title">Contact Support</h1>
                <p class="help-prompt">For any problem with your account, security concerns, or questions about our policy,
                    we're happy to help !</p>
                <form action="post" class="help-form">
                    <div class="all-questions">
                        <div class="help-question">
                            <label for="fname" class="help-label">Your Name * </label>
                            <input type="text" id="fname" name="fname" class="help-input" placeholder="..."><br>
                        </div>
                        <div class="help-question">
                            <label for="fname" class="help-label">Your Email * </label>
                            <input type="text" id="fname" name="fname" class="help-input" placeholder="..."><br>
                        </div>
                        <div class="help-question">
                            <label for="fname" class="help-label">Summary * </label>
                            <input type="text" id="fname" name="fname" class="help-input"
                                placeholder="Give us a brief description of what's happening."><br>
                        </div>
                        <div class="help-question">
                            <label for="fname" class="help-label">Add more details * </label>
                            <textarea name="" id="" cols="30" rows="10" class="help-input"
                                placeholder="If you have more specific info, add it here."></textarea><br>
                        </div>
                        <div class="help-question">
                            <label for="fname" class="help-label">Page Link </label>
                            <input type="text" id="fname" name="fname" class="help-input"
                                placeholder="Paste the link to where the issue is happening."><br>
                        </div>
                        <div class="help-question">
                            <label for="fname" class="help-label">Upload Screenshots</label>
                            <div id="drop_zone" ondrop="dropHandler(event);" ondragover="dragOverHandler(event);"
                                class="help-input">
                                <p style="color: rgba(27, 27, 27, 0.473);">Drag one or more files here...</p>
                            </div>
                        </div>
                    </div>

                </form>
                <p class="help-prompt">Thank you for your feedback !</p>

            </div>
        </div>
        <a id="TopBtn" href="#top" class="fa fa-angle-double-up hide" style="font-size: 24px"><font-awesome-icon icon="fa-solid fa-arrow-up" size="xs" style="color: #fff0fe;" /></a>        <footer>
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
    name: "HelpPage",
    components: {
        DarkLightMode,
        UserMenu
    },
    methods:{
        dropHandler(ev) {
        console.log("File(s) dropped");

        // Prevent default behavior (Prevent file from being opened)
        ev.preventDefault();

        if (ev.dataTransfer.items) {
            // Use DataTransferItemList interface to access the file(s)
            [...ev.dataTransfer.items].forEach((item, i) => {
                // If dropped items aren't files, reject them
                if (item.kind === "file") {
                    const file = item.getAsFile();
                    console.log(`… file[${i}].name = ${file.name}`);
                }
            });
    mounted(){
        var thisID = document.getElementById("TopBtn");
        var myScrollFunc = function () {
        var y = window.scrollY;
        if (y >= 300) {
            thisID.className = "fa fa-angle-double-up show";
        } else {
            thisID.className = "fa fa-angle-double-up hide";
        }
    },

    dragOverHandler(ev) {
        console.log("File(s) in drop zone");

        // Prevent default behavior (Prevent file from being opened)
        ev.preventDefault();
    };
        window.addEventListener("scroll", myScrollFunc);
    }
    }
};
// window.onload = function () {
//     function dropHandler(ev) {
//         console.log("File(s) dropped");

//         // Prevent default behavior (Prevent file from being opened)
//         ev.preventDefault();

//         if (ev.dataTransfer.items) {
//             // Use DataTransferItemList interface to access the file(s)
//             [...ev.dataTransfer.items].forEach((item, i) => {
//                 // If dropped items aren't files, reject them
//                 if (item.kind === "file") {
//                     const file = item.getAsFile();
//                     console.log(`… file[${i}].name = ${file.name}`);
//                 }
//             });
//         } else {
//             // Use DataTransfer interface to access the file(s)
//             [...ev.dataTransfer.files].forEach((file, i) => {
//                 console.log(`… file[${i}].name = ${file.name}`);
//             });
//         }
//     }

//     function dragOverHandler(ev) {
//         console.log("File(s) in drop zone");

//         // Prevent default behavior (Prevent file from being opened)
//         ev.preventDefault();
//     }
// };
</script>

<style></style>