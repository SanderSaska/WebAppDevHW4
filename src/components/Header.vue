<template>
  <div class="header">
    <div class="title">Header</div>
    <nav>
      <router-link to="/api/allposts">Posts</router-link> |
      <router-link to="/api/addpost">Add a Post</router-link> |
      <router-link to="/api/signup">SignUp</router-link> |
      <router-link to="/api/login">Login</router-link> |
      <router-link to="/api/contactUs">Contacts</router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: "header",
};
</script>

<style scoped>

.header {
  display: flex;
  background-color: gray;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  height: 18vh;
}

.title {
  font-size: 30px;
  font-weight: bold;
}
</style>
