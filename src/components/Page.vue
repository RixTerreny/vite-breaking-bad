
<template>
<div class="container mt-5">
    <select class="form-select w-25 mb-4 ms-2" aria-label="Default select example">
        <option selected>Select category</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>

    <div class="bg-white text-white p-5 d-flex flex-column justify-content-center" >
        <div class="numero-personaggi p-3">{{("Found "+store.count+" characters")}}</div>

        <div class="row mt-4 g-2">
            <div v-for="(element,i) in store.results" class="card col-3 bg-card rounded-0 text-center mx-1" style="width: 18rem;">
                <h5 class="mt-4">{{element.name}}</h5>
                <div class="card-body">
                    <p class="card-text">{{"Altezza: "+element.height+" cm" }}</p>
                    <p class="card-text">{{"Peso: "+element.mass+" Kg" }}</p>
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
        }
    },
    created(){
        axios.get("https://swapi.dev/api/people/")
        .then( resp=> {
            console.log(resp.data);
            this.store= resp.data;
        }); 
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