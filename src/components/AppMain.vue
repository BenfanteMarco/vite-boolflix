<script>
import {store} from '../store.js'
export default {
    name: 'AppMain',
    data(){
        return{
            store
        }
    },
    methods: {
        getFlag(flag) {
            if (flag == "en") {
                return "fi fi-gb"
            }
            if (flag == "it") {
                return "fi fi-it"
            }
        },
        getPoster(path) {
            let imgPath = store.posterPath + path
            return imgPath
        },
        getStar(vote) {
            let stars = vote.toFixed() / 2
            return stars
        }
    },
}
</script>
<template lang="">
   <main>
    <div class="film mt-3" v-if="store.movies.length > 0">
        <div class="container">
            <div class="row">
                <div class="col-12 justify-content-center mb-3">
                    <h2 class="text-center" >FILM</h2>
                </div>
                <div class="col-3 d-flex align-items-center text-center flex-column gap-2 mb-3" v-for="film, index in store.movies" :key="index">
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <img :src="getPoster(film.poster_path)" alt="" class="img-fluid">
                            </div>
                            <div class="flip-card-back">
                                <h2> TITLE: {{ film.title }} </h2>
                                <h3> ORIGINAL: {{ film.original_title }} </h3>
                                <span :class="getFlag(film.original_language)"></span>
                                <div>
                                    <i class="fas fa-star" :class="getStar(film.vote_average) >= 1 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(film.vote_average) >= 2 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(film.vote_average) >= 3 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(film.vote_average) >= 4 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(film.vote_average) == 5 ? 'gold' : ''"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div id="tvseries" v-if="store.series.length > 0">
        <div class="container">
            <div class="row">
                <div class="col-12 justify-content-center mb-3">
                    <h2 class="text-center" >SERIES</h2>
                </div>
                <div class="col-3 d-flex align-items-center text-center flex-column gap-2 mb-3" v-for="show, index in store.series" :key="index">
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <img :src="getPoster(show.poster_path)" alt="" class="img-fluid">
                            </div>
                            <div class="flip-card-back">
                                <h2> TITLE: {{ show.name }} </h2>
                                <h3> ORIGINAL: {{ show.first_air_date }} </h3>
                                <span :class="getFlag(show.original_language)"></span>
                                <div>
                                    <i class="fas fa-star" :class="getStar(show.vote_average) >= 1 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(show.vote_average) >= 2 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(show.vote_average) >= 3 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(show.vote_average) >= 4 ? 'gold' : ''"></i>
                                    <i class="fas fa-star" :class="getStar(show.vote_average) == 5 ? 'gold' : ''"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
   </main>
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';

    main {
    height: calc(100vh - 75px);
    overflow: auto;
    background-color: rgb(22, 22, 22);
        h1{
            color: white;
        }
        h2{
            color: white;
        }
        h3{
            color: white;
        }
        .fa-star {
            color: white;
        }
        .gold {
            color: gold;
        }
        .flip-card {
            perspective: 1000px;
            width: 300px;
            height: 450px;
        }
        .flip-card-inner {
            position: relative;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: transform 0.8s;
            transform-style: preserve-3d;
        }
        .flip-card:hover .flip-card-inner {
            transform: rotateY(180deg);
        }
        .flip-card-front, .flip-card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
        }
        .flip-card-front {
            background-color: #bbb;
            color: black;
        }
        .flip-card-back {
            transform: rotateY(180deg);
            border: 1px solid white;
        }
    }

</style>