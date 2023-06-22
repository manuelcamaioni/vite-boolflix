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
                    <li>
                        Voto: <em>{{ Math.round(movie.vote_average / 2) }}</em>
                    </li>
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
            let baseUrl = "https://image.tmdb.org/t/p/w500";
            baseUrl += imgPath;
            console.log(baseUrl);
            return baseUrl;
        },
    },
};
</script>

<style lang="scss" scoped></style>
