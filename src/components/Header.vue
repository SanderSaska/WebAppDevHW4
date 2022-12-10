<template>
  <div class="header">
    <h1>Header</h1>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/contactUs">Contacts</router-link> |
      <router-link to="/signup">Signup</router-link> |
      <router-link to="/login">Login</router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: "header",
};
</script>

<style scoped>
div {
  display: flex;
  background-color: grey;
  flex-direction: column;
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
</style>
