<template>
    <div>
        <ol>
            <li v-for="movie in store.MoviesList">
                <ul>
                    <li>
                        <img :src='getImagePath(movie.poster_path)' alt="" />
                    </li>
                    <li>
                        Titolo: <em>{{ movie.title }}</em>
                    </li>
                    <li>
                        Titolo originale: <em>{{ movie.original_title }}</em>
                    </li>
                    <li>
                        Lingua:
                        <em>{{
                            movie.original_language === "en"
                            ? this.getUnicodeFlagIcon("US")
                            : this.getUnicodeFlagIcon(
                                movie.original_language
                            )
                        }}</em>
                    </li>
                    <ul class="d-flex ps-0">
                        <li v-for="icon in  Math.round(series.vote_average / 2)">
                            <i class="bi bi-star-fill pe-2"></i>
                        </li>
                    </ul>
                </ul>
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

<style lang="scss" scoped></style>
