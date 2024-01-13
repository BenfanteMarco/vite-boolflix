<script>
import { store } from './store';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
  components: {
    AppHeader,
    AppMain,
  },
  data(){
    return{

    }
  },
  methods: {
    getMovies(){
      let searchMovies = store.movieApi;
      if(store.search !== ''){
        searchMovies += `&query=${store.search}`
      }
      axios.get(searchMovies).then((response) => {
        this.store.movies = response.data.results
      });
    }
  }
}
</script>
<template lang="">
  <AppHeader @filterMovie="getMovies()" />
  <AppMain />
</template>
<style lang="scss">
  @use './styles/generals.scss';
</style>