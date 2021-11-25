<template>
  <b-col>
    <h2>Add a Festival</h2>
    
  </b-col>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'FestivalsCreate',
    data() {
      return {         
        festivals: []
      };
    },
    mounted() {
      this.createFestival();
    },
    methods: {
      createFestival() {
        axios.post(`http://festivals-api.herokuapp.com/api/festivals`)
          .then((response) => {
            console.log(response.data)
            this.festivals = response.data
          })
          .catch(error => console.log(error))
      }
    }
  };
</script>
<style scoped>
  .btn {
    margin-bottom: 10px;
  }
</style>