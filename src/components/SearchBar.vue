<template>
    <section>
        <input type="text" v-model="search" />
        <button
            type="submit"
            @click="apiCall(this.search)"
            class="btn btn-primary">
            Cerca
        </button>
    </section>
</template>

<script>
import { store } from "../store";
import axios from "axios";

export default {
    data() {
        return {
            search: "",
            apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=256550ff1fdca66f331fdd0d6cec4eef",
            Movies: [],
            store,
        };
    },
    methods: {
        apiCall(searchArg) {
            axios
                .get(this.apiUrl, {
                    params: {
                        query: searchArg,
                    },
                })
                .then((response) => {
                    // handle success

                    this.store.MoviesList = response.data.results;

                    console.log(this.store.MoviesList);
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
            this.search = "";
        },
    },
};
</script>

<style lang="scss" scoped></style>
