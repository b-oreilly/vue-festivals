<template>
  <b-col>
    <h2>Festivals</h2>
    <b-button :to="{ name: 'festivals_create' }" variant="primary" class="float-right">Create</b-button>
    <div>
      <b-table responsive striped hover head-variant="dark" :items="festivals" :fields="headings">
        <template #cell(title)="data">
          <router-link :to="{ name: 'festivals_show', params: {id: data.item._id }}"> {{ data.value }} </router-link>
        </template>
        <template #cell(start_date)="data">
          {{ new Date(data.value).toLocaleString() }}
        </template>
        <template #cell(end_date)="data">
          {{ new Date(data.value).toLocaleString() }}
        </template>
      </b-table>
    </div>
    <!-- <b-card-group columns>
      <b-card bg-variant="light" v-for="festival in festivals" :key="festival.id" :img-alt="festival.title">
        <b-card-text>
          <router-link :to="{ name: 'festivals_show', params: {id: festival._id}}"> {{ festival.title }} </router-link>
        </b-card-text>
      </b-card>
    </b-card-group> -->
  </b-col>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Index',
    data() {
      return {
        headings: [{
            key: 'title',
            sortable: true
          },
          'description',
          'city',
          'start_date',
          'end_date'
        ],
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
<style scoped>
  .btn {
    margin-bottom: 10px;
  }
</style>