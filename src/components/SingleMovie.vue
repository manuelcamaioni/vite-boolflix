<template>
    <h2 v-show="store.MoviesList.length !== 0">Movies</h2>
    <ol class="ps-0">
        <li v-for="movie in store.MoviesList" class="container-media">
            <div class="media-list d-flex">
                <div class="thumbnail">
                    <img :src="getImagePath(movie.poster_path)" :alt="movie.name + ' missing image'"
                        v-if="movie.poster_path !== null" class="poster">
                    <img src="../assets/img-not-found.jpg" alt="" v-else>
                </div>
                <div class="overlay">
                    <div class="desc-box d-flex flex-column">
                        <span>Titolo: <em>{{ movie.title }}</em></span>
                        <span>Titolo originale: <em>{{ movie.original_title }}</em></span>
                        <span>Lingua:
                            <em>{{
                                this.getUnicodeFlagIcon(movie.original_language === "en" ? "gb" :
                                    movie.original_language) }}</em></span>
                        <div class="rating d-flex ps-0">
                            <span v-for="icon in  Math.round(movie.vote_average / 2)">
                                <i class="bi bi-star-fill pe-2"></i>
                            </span>
                        </div>
                    </div>
                </div>
            </div>

        </li>
    </ol>
</template>

<script>
import { store } from "../store";
import getUnicodeFlagIcon from "country-flag-icons/unicode";
export default {
    props: {
        Movies: Array,
    },

    data() {
        return {
            store,
            getUnicodeFlagIcon,
        };
    },
    methods: {
        getImagePath: function (imgPath) {
            let baseUrl = "https://image.tmdb.org/t/p/w200";
            baseUrl += imgPath;
            return baseUrl;
        },
    },
};
</script>

<style lang="scss" scoped></style>
