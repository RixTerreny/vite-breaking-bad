
<template>
<div class="container my-5">
    <select @change="selectedGender" v-model="gender" class="form-select w-25 mb-4 ms-2" aria-label="Default select example">
        <option selected disabled="true">Select category</option>
        <option value="">All</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="unknow">Unknow</option>
    </select>

    <div class="bg-white text-white p-5" >
        <div class="numero-personaggi p-3">{{("Found "+store.info.count+" characters")}}</div>

        <div class="row mt-4 g-2 p-2">
            <div v-for="(element,i) in store.results" class="card col-3 bg-card rounded-0 text-center mx-1 p-2" style="width: 18rem; " :key="i">
                <img :src="element.image" alt="">
                <h5 class="mt-4">{{element.name}}</h5>
                <div class="card-body">
                    <p class="card-text">{{"Gender: "+element.gender }}</p>
                    <p class="card-text">{{"Status: "+element.status }}</p>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import axios from "axios";
import {store} from "../store"
export default{
    data(){
        return{
            store,
            gender:"Select category",
        }
    },
    created(){
        let currentPage=0;
        axios.get("https://rickandmortyapi.com/api/character"+"?page="+currentPage)
        .then( resp=> {
            this.store.results= resp.data.results;
            this.store.info= resp.data.info;
            console.log(this.store);
        }); 
    },
    methods:{
        selectedGender(){
            this.$emit("search", this.gender);
        }
    }
}
import 'bootstrap/dist/css/bootstrap.min.css'
</script>


<style lang="scss">
@use '../styles/general.scss' as *;
.numero-personaggi{
    background-color: $not-main;
}

.bg-card{
    background-color: $main;
}
</style>