<template>
    <div>
        <ol>
            <li v-for="series in store.SeriesList">
                <ul>
                    <li>
                        Titolo: <em>{{ series.name }}</em>
                    </li>
                    <li>
                        Titolo originale: <em>{{ series.original_name }}</em>
                    </li>
                    <li>
                        Lingua:
                        <em>{{
                            series.original_language === "en"
                                ? this.getUnicodeFlagIcon("US")
                                : this.getUnicodeFlagIcon(
                                      series.original_language
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
};
</script>

<style lang="scss" scoped></style>
