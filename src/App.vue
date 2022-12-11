<script>
import axios from "axios";
import {store} from "./store"
export default{
  components: {Page},
  data(){
    store
  },
  methods:{
    searchGender(filtri){
      axios.get("https://rickandmortyapi.com/api/character/?gender="+filtri)
        .then( resp=> {
          this.store= resp.data;
          console.log(this.store);
        }); 
    }
  }
}
import 'bootstrap/dist/css/bootstrap.min.css'
import Page from './components/Page.vue';
</script>

<template>
<div class="text-white">
  <h1 class="ms-3 mt-2">Breacking Rick Api</h1>
</div>
<Page @search="searchGender"/>
</template>

<style lang="scss">
@use './styles/general.scss' as *;
body{
  background-color: $main;
}
</style>
