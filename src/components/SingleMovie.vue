<template>
    <div>
        <h2>Movies</h2>
        <ol class="d-flex flex-wrap ps-0">
            <li v-for="movie in store.MoviesList" class="d-flex ">
                <div class="media-list d-flex">
                    <div class="thumbnail">
                        <img :src="getImagePath(movie.poster_path)" :alt="movie.name + ' missing image'"
                            v-if="movie.poster_path !== null">
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
            console.log(baseUrl);
            return baseUrl;
        },
    },
};
</script>

<style lang="scss" scoped>
li {
    color: white;

    width: calc(100% / 4 - 1rem);
    margin: 0 .5rem;

    div.media-list {
        position: relative;

        width: 100%;

        div.overlay {
            opacity: 0;
        }

    }

    div.overlay {
        position: absolute;
        width: 100%;
        height: 100%;
        right: 0;
        bottom: 0;
        top: 0;
        left: 0;

    }

    div.media-list:hover div.overlay {
        opacity: 1;
        background-color: rgba(0, 0, 0, .4);
        transition: background-color .5s;
    }


    .thumbnail {
        border-radius: .3rem;
        overflow: hidden;
        height: 60vh;
        width: 100%;


        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

}
</style>
