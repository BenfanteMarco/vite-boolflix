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
      store
    }
  },
  methods: {
    getMovies(vote){
      let searchMovies = store.movieApi;
      let searchSeries = store.seriesApi;
      if(store.search !== ''){
        searchMovies += `&query=${store.search}`
        searchSeries += `&query=${store.search}`
      }
      axios.get(searchMovies).then((response) => {
        this.store.movies = response.data.results
      });
      axios.get(searchSeries).then((response) => {
        this.store.series = response.data.results
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