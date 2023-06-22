<template>
    <div class="container-media">
        <div v-for="series in store.SeriesList" class="media-list d-flex">
            <div class="thumbnail">
                <img :src="getImagePath(series.poster_path)" :alt="series.name + ' missing image'"
                    v-if="series.poster_path !== null" class="poster">
                <img src="../assets/img-not-found.jpg" alt="" class="not-found-poster" v-else>
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
                        <span v-for="icon in starRating(series.vote_average)">
                            <i class="bi bi-star-fill pe-2"></i>
                        </span>
                    </div>
                    <span class="overview">{{ series.overview }}</span>
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
