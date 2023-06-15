<template>
  <div>
    <div class="imgcontainer">
      <img src="https://cdn-icons-png.flaticon.com/512/295/295128.png" alt="Avatar" class="avatar">
    </div>

    <div class="container">
      <label for="uname"><b>Email</b></label>
      <input type="text" v-model="email" placeholder="Enter Email" name="uname" required>

      <label for="psw"><b>Password</b></label>
      <input type="password" v-model="password" placeholder="Enter Password" name="psw" required>

      <button type="button" @click="login">Login</button>
      <label>
        <input type="checkbox" checked="checked" name="remember"> Remember me
      </label>
    </div>

    <div class="container" style="background-color:#f1f1f1">
      <button type="button" class="cancelbtn">Cancel</button>
      <span class="psw">Create an <a href="/#/register">Account?</a></span>
    </div>
  </div>
</template>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}

form {
  border: 3px solid #f1f1f1;
}

input[type=text],
input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

button {
  background-color: #04AA6D;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

button:hover {
  opacity: 0.8;
}

.cancelbtn {
  width: auto;
  padding: 10px 18px;
  background-color: #f44336;
}

.imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
}

img.avatar {
  width: 10%;
  border-radius: 50%;
}

.container {
  padding: 16px;
  margin: 0 auto;
  max-width: 300px;
}

span.psw {
  float: right;
  padding-top: 16px;
}

/* Change styles for span and cancel button on extra small screens */
@media screen and (max-width: 300px) {
  span.psw {
    display: block;
    float: none;
  }

  .cancelbtn {
    width: 100%;
  }
}
</style>

<script>
import axios from 'axios'


export default {
  name: "LoginForm",
  data() {
    return {
      email: "",
      password: ""
    }
  },
  methods: {
    login() {
      var url = 'http://localhost:5083/api/User/SignIn'
      var data = {
        email: this.email,
        password: this.password
      }

      axios.post(url, data)
        .then((response) => {
          console.log(JSON.stringify(response));
          this.$q.notify({
            message: "Inicio de sesión exitoso",
            color: 'green',
            position: 'top',
            timeout: 5000
          })
          this.$router.push("/dashboard")
        }).catch(error => {
          this.$q.notify({
            message: error.message,
            color: 'red',
            position: 'top',
            timeout: 5000
          })

        })

      console.log("Login.......")
    },
    goToRegister() {
      this.$router.push("/register")
    }
  }


}


</script>
