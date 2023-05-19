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
        <div class="Profile-page-container">
            <div class="edit-profile-container">
                <div class="formContainer">
                    <div class="loginContainer">
                        <div class="loginForm">
                            <form @submit.prevent action="" method="post">
                                <h2 class="List-Title">Edit Profile</h2>
                                <div class="loginInputBox">
                                <input v-model="txtFName" type="text" name="txtFName" :placeholder="placeholderFName"><br>
                                </div>
                                <div class="loginInputBox">
                                <input v-model="txtEmail" type="email" name="txtEmail" :placeholder="placeholderEmail"><br>
                                </div>
                                <div class="error-message-profile">{{ message }}</div>
                                <div class="loginInputBox" style="margin-left: -60px;">
                                <input @click="updateInformation" type="submit" value="Update Information" name="btnUpdate">
                                </div>
                            </form>
                            <p class="forgotPswd">Change password ?<router-link to="/reset-password-page">Reset</router-link>
                            </p>
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
export default {
  name: 'ProfilePage',
  data() {
    return {
      txtFName: '',
      txtEmail: '',
      message: '',
      placeholderFName: 'First name',
      placeholderEmail: 'Email Address',
    };
  },
  methods: {
  updateInformation() {
    const token = localStorage.getItem('token');
    console.log(token);
    
    fetch("api/api/auth/profile", {
      method: 'PATCH',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer ' + token
      },
      body: JSON.stringify({ txt_FName: this.txtFName, txt_Email: this.txtEmail })
    })
    .then(response => {
        console.log(this.txtFName)
      if (response.ok) {
        this.message = 'Information updated';
      } else {
        throw new Error('Error updating information');
      }
      
      return response.json();
    })
    .then(data => {
      console.log('Response:', data);
    })
    .catch(error => {
      console.log('Error:', error);
    });
  },
},
  mounted() {
    const token = localStorage.getItem('token');
    console.log(token);
    fetch('api/api/user', {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json',
        Authorization: 'Bearer ' + token,
      },
    })
      .then((response) => {
        if (response.ok) {
          return response.json();
        } else {
          return response.json().then((error) => {
            throw new Error(JSON.stringify(error));
          });
        }
      })
      .then((data) => {
        this.txtFName = data.name;
        this.txtEmail = data.email;
        this.placeholderFName = data.name;
        this.placeholderEmail = data.email;
      })
      .catch((error) => {
        let errorMessage;
        try {
          errorMessage = JSON.parse(error.message);
        } catch {
          errorMessage = {
            message: 'An error occurred while processing your request.',
          };
        }
        this.message = errorMessage.message;
      });
  },
};
</script>


<style></style>