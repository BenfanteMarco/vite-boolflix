<script>
import {store} from '../store.js'
export default {
    name: 'AppMain',
    data(){
        return{
            store
        }
    }
}
</script>
<template lang="">
   <main>
    <div class="container">
        <div class="row">
            <div class="col-2 d-flex align-items-center text-center flex-column gap-2 mb-3" v-for="film, index in store.movies" :key="index">
                <h2> TITLE: {{ film.title }} </h2>
                <h3> ORIGINAL: {{ film.original_title }} </h3>
                <p> LANGUAGE: {{ film.original_language}} </p>
                <p> VOTE: {{ film.vote_average }} </p>
            </div>
        </div>
    </div>
   </main>
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';
</style>