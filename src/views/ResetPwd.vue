<template>
  <!-- <?php
session_start();
include 'dbConn.php';

if(isset($_POST['btnChange'])){
    $newpassword=md5($_POST['newpassword']);
    $uid=$_SESSION['uid'];
    $query="UPDATE `tblusers` SET `password`='$newpassword' WHERE ID='$uid'";
    $result=mysqli_query($connection,$query);
    header("Location: index.php");
}

mysqli_close($connection);
?> -->


<body>
    <section class="ResetPage">
        <div class="resetBox">
            <div class="loginContainer">
                <div class="loginForm">
                    <h2>New Password</h2>
                    <p class="NewPswdPrompt">Please enter a <bold>personnalized password </bold>to ensure maximum protection.</p>
                    <form action="" method="post">
                        <div class="loginInputBox">
                            <input type="password" placeholder="Password" name="newpassword">
                        </div>
                        <div class="loginInputBox">
                            <input id="NewPwdbtn" type="submit" value="Edit" name="btnChange">
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </section>
</body>


</template>

<script>
export default {
    name: 'ResetPwdPage'
}
</script>

<style>

</style>