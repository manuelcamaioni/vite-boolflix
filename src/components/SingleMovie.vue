<template>
    <div>
        <ol>
            <li v-for="movie in store.MoviesList">
                <ul>
                    <li>
                        Titolo: <em>{{ movie.title }}</em>
                    </li>
                    <li>
                        Titolo originale: <em>{{ movie.original_title }}</em>
                    </li>
                    <li>
                        Lingua:
                        <em>{{
                            this.getUnicodeFlagIcon(movie.original_language)
                        }}</em>
                    </li>
                    <li>
                        Voto: <em>{{ movie.vote_average }}</em>
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
};
</script>

<style lang="scss" scoped></style>
