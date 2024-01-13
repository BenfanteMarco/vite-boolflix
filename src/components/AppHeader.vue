<script>
import { store } from '../store';
export default {
    name: 'AppHeader',
    data(){
        return{
            store
        }
    }
            
}
</script>
<template lang="">
    <header>
        <div class="container">
            <div class="row">
                <div class="col-12 d-flex d-flex justify-content-between">
                    <h1>boolflix</h1>
                    <div class="separate d-flex align-items-center gap-3">
                        <input type="text" name="search" id="search" v-model="store.search" placeholder="Search..">
                        <button class="btn btn-danger" @click="$emit('filterMovie')">Search</button>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';

    header {
    background-color: black;
    width: 100%;
    position: fixed;
    #search {
        border-radius: 20px;
        border: 1px solid white;
        background-color: transparent;
        color: white;
        padding: 5px;
    }
    h1 {
        color: red;
        padding: 10px;
        text-transform: uppercase;
        margin-bottom: 0px;
    }
}
</style>