<template>
  <!-- <nav>
    <router-link to="/api/allposts">Posts</router-link> |
    <router-link to="/api/addpost">Add a Post</router-link> |
    <router-link to="/api/signup">SignUp</router-link> |
    <router-link to="/api/login">Login</router-link> |
    <router-link to="/api/contactUs">Contacts</router-link>
  </nav> -->
  <router-view />
</template>

<script>
export default {
  name: "App",
   methods: {
    Logout() {
      fetch("http://localhost:3000/auth/logout", {
          credentials: 'include', //  Don't forget to specify this if you need cookies
      })
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        console.log('jwt removed');
        //console.log('jwt removed:' + auth.authenticated());
        this.$router.push("/login");
        //location.assign("/");
      })
      .catch((e) => {
        console.log(e);
        console.log("error logout");
      });
    },
  }, 
};
</script>

<style>
body {
  height: 100vh;
  width: 100vw;
  margin: 0 !important;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  width: 100vw;
}

nav {
  padding: 15px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
button{
  margin-top: 30px;
  border-radius: 36px;
  background: #FEE996;
  border:0;
  font-weight: 700;
  font-size: 0.8em;
  display: block;
  padding: 10px 16px;
  letter-spacing: 2px;
}
.container {
  display: flex;
  justify-content: center;
}

div {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box; 
}
</style>
