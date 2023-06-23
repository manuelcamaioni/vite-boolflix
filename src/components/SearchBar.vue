<template>
    <div class="d-flex align-items-center search-container">
        <input type="text" v-model="search" @keyup.enter="apiCall(this.search)" />
        <button type="submit" @click="apiCall(this.search)" class="btn btn-danger d-flex">
            <i class="bi bi-search m-auto"></i>
        </button>
    </div>
</template>

<script>
import { store } from "../store";
import axios from "axios";

export default {
    data() {
        return {
            search: "",
            apiUrlMovies:
                "https://api.themoviedb.org/3/search/movie?api_key=256550ff1fdca66f331fdd0d6cec4eef",
            apiUrlSeries:
                "https://api.themoviedb.org/3/search/tv?api_key=256550ff1fdca66f331fdd0d6cec4eef",

            store,
        };
    },
    methods: {
        apiCall(searchArg) {
            axios
                .get(this.apiUrlMovies, {
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

            axios
                .get(this.apiUrlSeries, {
                    params: {
                        query: searchArg,
                    },
                })
                .then((response) => {
                    // handle success

                    this.store.SeriesList = response.data.results;
                    console.log(this.store.SeriesList);
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

<style lang="scss" scoped>
.search-container>* {
    margin: 0 .5rem;
}

button {
    width: 35px;
    height: 35px;
    border-radius: 50%;
    padding: 0;

    .bi {
        line-height: 0;
    }
}
</style>
