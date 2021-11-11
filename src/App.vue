<template>
  <div>
    <NavBar />
    <b-container>
      <br />
      <b-row>
        <router-view />
      </b-row>
      <Footer />
    </b-container>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar.vue"
import Footer from "@/components/Footer.vue"

export default {
  name: "App",
  components: {
    NavBar,
    Footer
  }
};
</script>

<style>

</style>
