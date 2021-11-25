<template>
  <div>
    <NavBar :loggedIn="loggedIn" v-on:logout="setLoggedOut" />
    <b-container>
      <br />
      <b-row>
        <router-view :loggedIn="loggedIn" v-on:login="setLoggedIn" />
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
    },
    data() {
      return {
        loggedIn: false
      }
    },
    created() {
      localStorage.getItem('token') ? this.loggedIn = true : this.loggedIn = false
    },
    methods: {
      setLoggedIn(token) {
        this.loggedIn = true
        localStorage.setItem('token', token)
      },
      setLoggedOut() {
        this.loggedIn = false
        localStorage.removeItem('token')
      }
    }
  }
</script>

<style>

</style>