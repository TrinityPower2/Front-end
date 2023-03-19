<template>
    <body>
        <!-- <?php if($_SESSION['admin']==1){?> -->
        <div class="FormPage">
            <div class="header-image">
                <img alt="Vue logo" src="../assets/TimeToDo1.png" class="VueLogo" />
            </div>
            <div class="FormBox">
                <div class="loginContainer">
                    <div class="loginForm">
                        <h2>Your Preferences</h2>
                        <form action="#" method="post">
                            <input type="hidden" name="nbquestion" style="display: none;"
                                value="<?php echo $row['nbquestion']; ?>">
                            <input type="hidden" name="question" style="display: none;"
                                value="<?php echo $row['question']; ?>">
                            <input type="hidden" name="answer" style="display: none;" value="<?php echo $row['answer']; ?>">
                            <input type="hidden" name="category" style="display: none;"
                                value="<?php echo $row['category']?>">
                            <input type="hidden" name="level" style="display: none;" value="<?php echo $row['level']?>">
                            <div class="loginInputBox">
                                <input type="text" name="txtNbQuestion" value="<?php echo $row['nbquestion']?>">
                            </div>
                            <div class="loginInputBox">
                                <input type="text" name="txtQuestion" value="<?php echo $row['question']?>">
                            </div>
                            <div class="loginInputBox">
                                <input type="text" name="txtAnswer" value="<?php echo $row['answer']?>">
                            </div>
                            <div class="loginInputBox">
                                <input type="text" name="txtCategory" value="<?php echo $row['category']?>">
                            </div>
                            <div class="loginInputBox">
                                <input type="text" name="txtLevel" value="<?php echo $row['level']?>">
                            </div>
                            <div class="loginInputBox">
                                <input type="submit" value="Update Information" name="btnUpdate">
                            </div>
                            <p class="forgotPswd">Skip for now ?<a href="./Register.html">Move on</a></p>
                        </form>
                    </div>
                </div>
            </div>
        </div>
        <footer style="margin-top: 0%;">
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
export default {
    name: 'EntryFormPage',
}
</script>

<style></style> <!-- <?php }else{?> 
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