<template>
    <h2 class="ps-2" v-show="store.MoviesList.length !== 0">Movies</h2>
    <div class="container-media">
        <div v-for="movie in store.MoviesList" class="media-list d-flex">
            <div class="thumbnail">
                <img :src="getImagePath(movie.poster_path)" :alt="movie.name + ' missing image'"
                    v-if="movie.poster_path !== null" class="poster">
                <img src="../assets/img-not-found.jpg" alt="" class="not-found-poster" v-else>

            </div>
            <div class="overlay">
                <div class="desc-box d-flex flex-column">
                    <span>Titolo: <em>{{ movie.title }}</em></span>
                    <span>Titolo originale: <em>{{ movie.original_title }}</em></span>
                    <span>Lingua:
                        <em>{{
                            this.getUnicodeFlagIcon(movie.original_language === "en" ? "gb" :
                                movie.original_language) }}</em></span>
                    <div class="rating d-flex align-items-center ps-0">
                        <span v-for="icon in  starRating(movie.vote_average)">
                            <i class="bi bi-star-fill pe-2"></i>
                        </span>
                        <span class="vote-count">{{ `(${movie.vote_count})` }}</span>
                    </div>
                    <span class="overview">{{ movie.overview }}</span>
                </div>
            </div>
        </div>

    </div>
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

        starRating: function (num) {
            let result = Math.round(num / 2);
            if (result === 0) {
                result = 1;
            }
            return result;

        }
    },


};
</script>

<style lang="scss" scoped></style>
