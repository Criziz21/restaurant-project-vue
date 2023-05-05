<template>
<Header />
<h1>Hello user, Welcome on Add Restaurant Page</h1>
<form class="add">
  <input type="text" v-model="restaurant.name" placeholder="Enter Name">
  <input type="text" v-model="restaurant.address" placeholder="Enter Adress">
  <input type="text" v-model="restaurant.contact" placeholder="Enter Contact">
  <button v-on:click="addRestaurant" type="button">Add Restaurant</button>
</form>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
  name:'AddRestaurant',
  components: {
    Header
  },
  data() {
    return {
      restaurant: {
        name:'',
        address:'',
        contact:''
      }
    }
  },
  methods: {
    async addRestaurant() {
      const result = await axios.post("http://localhost:3000/restaurant", {
        name:this.restaurant.name,
        address:this.restaurant.address,
        contact:this.restaurant.contact
      });
      if(result.status == 201) {
        this.$router.push({name:'HomePage'});
      }
    }
  },
  mounted() {
    let user = localStorage.getItem('user-info')
    if(!user) {
      this.$router.push({name:'SignUp'});
    }
  }
}
</script>

<style>
</style>
