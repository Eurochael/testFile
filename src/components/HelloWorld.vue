<template>
  <div class="hello">
    <input v-model="message" placeholder="여기를 수정해보세요" v-on:change="fetchData(message)">

    <div>  {{Fetch_DB}}</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'HelloWorld',
  data(){
    return {
      message: 1, 
      Fetch_DB: {
        color : "#98B2D1",
        id : 1,
        name :"cerulean",
        pantone_value :"15-4020",
        year : 2000
      }
    }
  },
  methods:{
    fetchData(message) {
      axios.get('https://reqres.in/api/user/' + message)
              .then(res => {
                this.Fetch_DB = res.data.data;
                console.log(this.Fetch_DB)
              })
    }
  }
}
</script>

