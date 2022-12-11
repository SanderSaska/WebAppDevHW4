<template>
  <Header />
  <div class="contactUs">
    <span>2022-2022</span>
    <span>Team AU</span>
    <span>© Copyright</span>
  </div>
  <Footer />
</template>

<script>
// @ is an alias to /src

import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "contactUs",
  components: {
    Header,
    Footer,
  },
};
</script>

<style scoped>
.contactUs {
  display: flex;
  padding: 20px;
  flex-direction: column;
  height: 70vh;
  justify-content: center;
}
</style>
