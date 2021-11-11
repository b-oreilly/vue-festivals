<template>
  <b-col>
    <h2>Festivals</h2>
    <b-card-group columns>
      <b-card bg-variant="light" v-for="festival in festivals" :key="festival.id" :img-alt="festival.title">
        <b-card-text>
           {{ festival.title }}
        </b-card-text>
      </b-card>
    </b-card-group>
  </b-col>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Index',
    data() {
      return {
        festivals: []
      };
    },
    mounted() {
      this.allFestivals();
    },
    methods: {
      allFestivals() {
        axios.get(`http://festivals-api.herokuapp.com/api/festivals`)
          .then((response) => {
            console.log(response.data)
            this.festivals = response.data
          })
          .catch(error => console.log(error))
      }
    }
  };
</script>