<template>
  <b-navbar toggleable="lg" type="light" variant="light">
    <b-container>
      <b-navbar-brand to="/">FestivalCloud</b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item :to="{ name: 'festivals_index' }">Festivals</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-container>
  </b-navbar>
</template>

<script>
  export default {
    name: "NavBar"
  };
</script>

<style>
    .navbar {
        margin-bottom: 10px;
        /* padding-left: 20px; */

    }

    b-nav-item-dropdown {
        list-style-type: none;
    }

    .navbar-toggler {
        border: 0px !important;
    }

    .navbar-toggler:focus {
        box-shadow: none !important;
    }</style>