<template>
  <Header />
  <div class="page">
    <form @submit.prevent="submitForm" v-if="!formSubmitted" class="signup">
      <span>Email</span>
      <input v-model="Email" type="email" placeholder="Email" /><br />
      <span>Password</span>
      <input v-model="password" type="password" placeholder="Password" /><br />
      <div v-if="Validation != '' && clicked" class="validation">
        <span>Password is not valid!</span><br />
        <span>Password criteria:</span><br />
        <span>{{ Validation }}</span>
      </div>
      <button @click="singup()">Signup</button>
    </form>
  </div>
  <Footer />
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import { CLOSING } from "ws";

export default {
  name: "HomeView",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      password: "",
      clicked: 0,
    };
  },
  computed: {
    Validation() {
      let output = "";
      let password = this.password;
      let arrayPassword = password.split("");

      if (!password || (8 > password.length && password.length < 14)) {
        output += " Lenght between 8-14\n";
      }

      if (password.search(/\d+/) === -1) {
        output += " One number\n";
      }

      if (!password || password[0]?.toUpperCase() !== password[0]) {
        output += " Upper case first letter\n";
      }

      if (password.search(/[a-z]+/) !== -1) {
        arrayPassword.splice(password.search(/[a-z]+/), 1);
        password = arrayPassword.join("");
        if (password.search(/[a-z]+/) === -1) {
          output += " Two lower case letters\n";
        }
      } else {
        output += " Two lower case letters\n";
      }

      if (!arrayPassword.includes("_")) {
        output += " One underscore";
      }

      return output;
    },
  },
  methods: {
    singup() {
      this.clicked += 1;
      if (!this.Validation) {
        this.$router.push("/");
      }
    },
  },
};
</script>

<style scoped>
Footer {
  bottom: 0px;
  width: 99vw;
  border-radius: 10px;
  display: flex;
  background-color: grey;
  position: fixed;
  justify-content: center;
}

Header {
  border-radius: 10px;
  font-size: 2em;
  font-weight: bold;
  background-color: rgb(220, 220, 220);
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 10px;
  padding-left: 20px;
}

.page {
  width: 100%;
  height: 50vh;
  margin: 10px 0;
  padding: 10px 0;
  background-color: grey;
  justify-content: center;
  align-items: center;
  vertical-align: middle;
}
.signup {
  display: flex;
  flex-direction: column;
  color: white;
  background-color: rgb(32, 70, 139);
  border: none;
  padding: 20px;
  width: 250px;
  align-items: center;
  margin: 50px auto;
  border-radius: 10px;
}

.validation {
  color: black;
  white-space: pre-wrap;
  text-align: left;
  background-color: #ffcccb;
  border: red solid 2px;
  border-radius: 10px;
  margin-bottom: 10px;
  padding: 5px;
}
</style>
