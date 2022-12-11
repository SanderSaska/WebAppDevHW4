<template>
  <Header />
  <div class="AllPosts">
    <div id="post-list">
      <div class="container">
        <button v-if="authResult" @click="Logout" class="center">Logout</button>
      </div>
      <ul>
        <div class="item" v-for="post in posts" :key="post.id">
          <a class="singlepost" :href="'/api/apost/' + post.id">
            <p class="date">{{ formatDate(post.date) }}</p>
            <p class="body">{{ post.body }}</p>
          </a>
        </div>
      </ul>
    </div>
    <div id="buttons">
      <button @click="this.$router.push('/api/addPost')" class="center">Add Post</button>
      <button @click="DeleteAll" class="center">Delete All</button>
    </div>
  </div>
  <Footer />
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import moment from 'moment';
import auth from "../../server/auth";
export default {
  name: "AllPosts",
  components: {},
    data() {
      return {
        posts: [],
        authResult: auth.authenticated()
      }
    },
  methods: {
    fetchPosts() {
      fetch(`http://localhost:3000/api/posts/`)
        .then((response) => response.json())
        .then((data) => (this.posts = data))
        .catch((err) => console.log(err.message));
    },
    Logout() {
      fetch("http://localhost:3000/auth/logout", {
        credentials: "include",
      })
        .then((response) => response.json())
        .then((data) => {
          console.log("jwt removed");
          location.assign("/"); // why redirect to the home directory?
        })
        .catch((e) => {
          console.log("error logout");
        });
    },
    DeleteAll() {
      fetch("http://localhost:3000/api/posts/", {
        method: "DELETE",
        headers: { "Content-Type": "application/json" },
      })
        .then((response) => {
          console.log(response.data);
          this.$router.go();
        })
        .catch((err) => {
          console.log(err.message);
        });
    },
    formatDate(value){
         if (value) {
           return moment(String(value)).format('DD-MM-YYYY')
          }
      },
  },
  mounted() {
    this.fetchPosts();
    console.log("mounted");
  },
  components: {
    Header,
    Footer,
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}

#buttons {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding-inline: 25vw;
}
.item {
  background: rgb(189, 212, 199);
  margin-bottom: 5px;
  padding: 3px 5px;
  border-radius: 10px;
}
#post-list {
  background: #6e8b97;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
  margin-bottom: 30px;
  padding: 10px 20px;
  margin: auto;
  width: 50%;
  border-radius: 20px;
}
#post-list ul {
  padding: 0;
}
#post-list li {
  display: inline-block;
  margin-right: 10px;
  margin-top: 10px;
  padding: 20px;
  background: rgba(255, 255, 255, 0.7);
}
</style>
