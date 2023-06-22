<template>
    <h2 v-show="store.SeriesList.length !== 0">TV Series</h2>
    <ol class="ps-0">
        <li v-for="series in store.SeriesList" class="container-media">
            <div class="media-list d-flex">
                <div class="thumbnail">
                    <img :src="getImagePath(series.poster_path)" :alt="series.name + ' missing image'"
                        v-if="series.poster_path !== null" class="poster">
                    <img src="../assets/img-not-found.jpg" alt="" v-else>
                </div>
                <div class="overlay">
                    <div class="desc-box d-flex flex-column">
                        <span>Titolo: <em>{{ series.name }}</em></span>
                        <span>Titolo originale: <em>{{ series.original_name }}</em></span>
                        <span>Lingua:
                            <em>{{
                                this.getUnicodeFlagIcon(series.origin_country[0] === undefined ? "n/d" :
                                    series.origin_country[0]
                                )
                            }}</em></span>
                        <div class="rating d-flex ps-0">
                            <span v-for="icon in  Math.round(series.vote_average / 2)">
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
