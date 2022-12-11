<template>
  <Header />
  <div class="container">
    <div class="form">
      <h3>Add a Post</h3>
      <label for="body">Body: </label>
      <input name="body" type="text" id="body" required v-model="post.body" />
      <button @click="addPost" class="addPost">Add Post</button>
    </div>
  </div>
  <Footer />
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "AddPost",
  data() {
    return {
      post: {
        body: "",
        date: "",
      },
    };
  },
  methods: {
    addPost() {
      var data = {
        date: new Date(),
        body: this.post.body,
      };
      fetch("http://localhost:3000/api/posts", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(data),
      })
      .then((response) => {
        console.log(response.data);
        this.$router.push("/api/allposts");
      })
      .catch((e) => {
        console.log(e);
        console.log("error");
      });
    },
  },
  components: {
    Header,
    Footer
  }
};
</script>

<style scoped>
.container {
  height: 70vh;
}
.form {
  width: 420px;
  margin: auto;
  background: rgb(167, 154, 154);
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
h3 {
  text-align: center;
  color: rgb(8, 110, 110);
}
label {
  color: rgb(8, 110, 110);
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.8em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid white;
  color: blue;
}
button {
  background: rgb(8, 110, 110);
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
  align-items: center;
  text-align: center;
}
</style>