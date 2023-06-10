<template>
  <div>
    <div class="imgcontainer">
      <img
        src="https://firebasestorage.googleapis.com/v0/b/esan2021.appspot.com/o/logo.png?alt=media&token=ebaf532a-4596-4ccb-a11e-d9fa5aab6790"
        alt="Avatar" class="avatar">
    </div>

    <div class="container">
      <label for="uname"><b>Email</b></label>
      <input type="text" v-model="email" placeholder="Enter email" name="uname" required>

      <label for="psw"><b>Password</b></label>
      <input type="password" v-model="password" placeholder="Enter Password" name="psw" required>

      <button @click="login">Login</button>
      <label>
        <input type="checkbox" checked="checked" name="remember"> Remember me
      </label> |
      Create an <a href="#">Account?</a>
    </div>
  </div>
</template>

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
    login: function () {
      var url = 'http://localhost:5211/api/User/SignIn'
      var data = {
        email: this.email,
        password: this.password
      }
      axios.post(url, data)
        .then(response => {
          console.log("Aquí va la respuesta " + JSON.stringify(response))
          localStorage.setItem("userResult",JSON.stringify(response.data))
          this.$q.notify({
            message: "Inicio de sesión correcta",
            color: "positive",
            position: "bottom",
            timeout: 3000
          });
          this.$router.push("/dashboard")
        }).catch(error => {
          console.log("Ocurrió un error " + error)
          localStorage.removeItem("userResult")
          this.$q.notify({
            message: "Ocurrió un error",
            color: "negative",
            position: "top",
            timeout: 3000
          });
        })
    }
  }

}

</script>

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
  width: 20%;
  border-radius: 50%;
}

.container {
  padding: 16px;
  margin: 0 auto;
  /* Agrega esta línea */
  max-width: 300px;
  /* Ajusta el ancho máximo según tus necesidades */
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
