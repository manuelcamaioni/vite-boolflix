<template>
    <div>
        <ol>
            <li v-for="series in store.SeriesList">
                <ul>
                    <li><img :src="getImagePath(series.poster_path)" :alt="series.name + ' missing image'"></li>
                    <li>
                        Titolo: <em>{{ series.name }}</em>
                    </li>
                    <li>
                        Titolo originale: <em>{{ series.original_name }}</em>
                    </li>
                    <li>
                        Lingua:
                        <em>{{
                            this.getUnicodeFlagIcon(series.origin_country[0] === undefined ? "n/d" :
                                series.origin_country[0]
                            )
                        }}</em>
                    </li>
                    <li>
                        Voto: <em>{{ series.vote_average }}</em>
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
