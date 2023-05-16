<template>
    <body>
        <div class="FormPage1">
            <div class="header-image">
                <img alt="Vue logo" style="opacity: 0.7;" src="../assets/TimeToDo1.png" class="VueLogo" />
            </div>

            <div class="FormBox">
                <div class="FormContainer">
                    <div class="Form-banner-container">
                        <div class="loginForm">
                            <h2>Your Preferences</h2>
                            <p class="Form-presentation"> <br> TimeToDo depends on an <i class="fa fa-bold" aria-hidden="true">algorithm</i>  to optimize your plannings. <br><br> The following questions will help us <i class="fa fa-bold" aria-hidden="true">taylor your planning</i> , depending on your needs :<br><br></p>
                                <p class="Form-question">On which timeslot is your lunch break ?</p>
                                <div class="loginInputBox">
                                    <input v-model = "Lunch1" @input="convertToISO($event, 'Lunch1')" type="time" step="900" name="txtQuestion" style="width:50%;"/>
                                    <input v-model = "Lunch2" @input="convertToISO($event, 'Lunch2')" type="time" step="900" name="txtQuestion" style="width:50%"/>
                                </div>
                                <p class="Form-question">On which timeslot is your diner break ?</p>
                                <div class="loginInputBox">
                                    <input v-model = "Dinner1" @input="convertToISO($event, 'Dinner1')" type="time" step="900" name="txtQuestion" style="width:50%"/>
                                    <input v-model = "Dinner2" @input="convertToISO($event, 'Dinner2')" type="time" step="900" name="txtQuestion" style="width:50%"/>
                                </div>
                                <p class="Form-question">What is your sleeping schedule ?</p>
                                <div class="loginInputBox">
                                    <input v-model = "Sleeping1" @input="convertToISO($event, 'Sleeping1')" type="time" step="900" name="txtQuestion" style="width:50%"/>
                                    <input v-model = "Sleeping2" @input="convertToISO($event, 'Sleeping2')" type="time" step="900" name="txtQuestion" style="width:50%"/>
                                </div>
                                <p class="Form-question">Would you rather have schedules in the morning or the afternoon ?</p>
                                <div class="Switch-container">
                                    <p class="Switch-label">Morning</p>
                                    <label class="switch">
                                        <input type="checkbox"  v-model="isMorningSelected">
                                        <span class="slider"></span>
                                    </label>
                                    <p class="Switch-label">Afternoon</p>
                                </div>
                                <br><br>
                                <p class = "message">{{ message }}</p>
                                <div class="loginInputBox FormInputBox">
                                    <input @click = "send" type="submit" value="Submit Information" name="btnUpdate" />
                                </div>
                                <p class="forgotPswd MoveOn">
                                    Skip for now ?<a href="/calendar-page">Move on</a>
                                </p>

                        </div>
                    </div>
                </div>
            </div>
        </div>
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
export default {
    name: "EntryFormPage1",
    data(){
          return{
            Questions: ["lunchtime", "dinnertime","sleeptime"],
            Lunch1 : "",
            Lunch2 : "",
            Dinner1 : "",
            Dinner2 : "",
            Sleeping1 : "",
            Sleeping2 : "",
            isMorningSelected : false,
            message :  "",
            name_timepref: "",
            start_time: "",
            length : "",
          }
        },

    methods:{
        convertToISO(event, field) {
            const time = event.target.value;
            const [hours, minutes] = time.split(':');
            const isoTime = `${hours.padStart(2, '0')}:${minutes.padStart(2, '0')}:00`;
            this[field] = isoTime;
        },
        send(){
            if(this.Lunch1 == "" || this.Lunch2 == "" || this.Dinner1 == "" || this.Dinner2 == "" || this.Sleeping1 == "" || this.Sleeping2 == "" ){
                this.message = "Please fill all the fields"
            }
            else{
            const lunchDuration = this.calculateDuration(this.Lunch1, this.Lunch2);
            const dinnerDuration = this.calculateDuration(this.Dinner1, this.Dinner2);
            const sleepingDuration = this.calculateDuration(this.Sleeping1, this.Sleeping2);
            const StartTime = [this.Lunch1, this.Dinner1, this.Sleeping1]
            const Duration = [lunchDuration, dinnerDuration, sleepingDuration]
            for (let i = 0; i < 3; i++) {
                const token = localStorage.getItem('token');
                console.log(token)
                fetch("http://127.0.0.1:8000/api/timepref", {
                    method: 'POST',
                    headers: {
                    'Content-Type': 'application/json',
                    'Authorization': 'Bearer ' + token
                    },
                    body: JSON.stringify({
                    name_timepref: this.Questions[i],
                    start_time: StartTime[i],
                    length: Duration[i]
                    })
                }).then((response)=>{
        
                if (response.ok) {
                    return response.json();
                }
                else {   
                        return response.json().then(error => {
                            throw new Error(JSON.stringify(error));
                    });
                }})
                
                .then((parsed) => {localStorage.setItem('token',parsed.token);
                })
                .then(()=>{this.$router.push('/calendar-page');})
                .catch((error) => {
                    let errorMessage;
                    try {
                        errorMessage = JSON.parse(error.message);
                    } catch {
                        errorMessage = {
                        message: 'An error occurred while processing your request.'
                        };
                        this.message = errorMessage.message;
                    }
                    if(errorMessage.status === false){

                        this.message = errorMessage.message;
                    }
                    else{
                        this.message = errorMessage.errors;
                    }
                
                    
                });
            }}}                
            ,
              
            calculateDuration(time1, time2) {
                const [hours1, minutes1] = time1.split(":").map(Number);
                const [hours2, minutes2] = time2.split(":").map(Number);

                const minutesTime1 = hours1 * 60 + minutes1;
                const minutesTime2 = hours2 * 60 + minutes2;

                return minutesTime2 - minutesTime1;
            }
      }

    }
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
    
