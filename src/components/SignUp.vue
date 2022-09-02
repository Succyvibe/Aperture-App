<template>
  <img class="logo" src="../assets/logo.jpg" />
  <h1>Sign Up for Free Now</h1>
  <div class="register">
    <input type="text" v-model="name" placeholder="enter your name" />
    <input type="text" v-model="email" placeholder="email" />
    <input type="password" v-model="password" placeholder="password" />
    <button @click="signUp">Sign Up</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      password: "",
      email: "",
    };
  },

  methods: {
    async signUp() {
      let result = await axios.post("http://localhost:3000/users", {
        name: this.name,
        email: this.email,
        password: this.password,
      });

      console.warn(result);
      if (result.status === 201) {
        alert("sign up successfull");
        localStorage.setItem("user-info", JSON.stringify(result.data));
      }
    },
  },
};
</script>

<style scoped>
.logo {
  width: 100px;
  margin-top: 30px;
  margin-bottom: 30px;
}

.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid rgba(255, 166, 0, 0.466);
}

.register input:active {
  border: none;
  outline: none;
}

.register button {
  width: 320px;
  height: 40px;
  border: 1px solid rgba(255, 166, 0, 0.466);
  background: rgba(255, 166, 0, 0.466);
  color: white;
  cursor: pointer;
}

.register button:hover {
  background: rgba(255, 166, 0, 0.582);
  transition: ease all 300ms;
}
</style>
