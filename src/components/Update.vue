<template>
<Header />
<h1>Hello user, Welcome on Update Restaurant Page</h1>
<form class="add">
  <input type="text" v-model="restaurant.name" placeholder="Enter Name">
  <input type="text" v-model="restaurant.address" placeholder="Enter Adress">
  <input type="text" v-model="restaurant.contact" placeholder="Enter Contact">
  <button v-on:click="updateRestaurant" type="button">Update Restaurant</button>
</form>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
  name:'UpdateRestaurant',
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
    async updateRestaurant() {
      const result = await axios.put("http://localhost:3000/restaurant/" + this.$route.params.id, {
        name:this.restaurant.name,
        address:this.restaurant.address,
        contact:this.restaurant.contact
      });
      if(result.status == 200) {
        this.$router.push({name:'HomePage'});
      }
    }
  },
  async mounted() {
    let user = localStorage.getItem('user-info')
    if(!user) {
      this.$router.push({name:'SignUp'});
    }
    const result = await axios.get(`http://localhost:3000/restaurant/${this.$route.params.id}`)
    this.restaurant = result.data
  }
}
</script>

<style>
</style>
