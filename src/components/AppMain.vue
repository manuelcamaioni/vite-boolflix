<template>
    <main>
        <SearchBar :Movies="Movies" />
        <SingleMovie :Movies="Movies" />
    </main>
</template>

<script>
import SearchBar from "./SearchBar.vue";
import SingleMovie from "./SingleMovie.vue";
import { store } from "../store";
import axios from "axios";

export default {
    components: {
        SearchBar,
        SingleMovie,
    },
    data() {
        return {
            Movies: [],
        };
    },
    methods: {},
    created() {},
};
</script>

<style lang="scss" scoped></style>
