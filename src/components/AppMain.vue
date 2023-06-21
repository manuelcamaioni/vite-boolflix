<template>
    <main>
        <SingleMovie />
        <SingleSeries />
    </main>
</template>

<script>
import SearchBar from "./SearchBar.vue";
import SingleMovie from "./SingleMovie.vue";
import SingleSeries from "./SingleSeries.vue";
import { store } from "../store";

export default {
    components: {
        SearchBar,
        SingleMovie,
        SingleSeries,
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
