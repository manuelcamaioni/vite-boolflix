<template>
    <main>
        <SingleMovie />
        <SingleSeries />

    </main>
</template>

<script>

import SingleMovie from "./SingleMovie.vue";
import SingleSeries from "./singleSeries.vue"

export default {
    components: {

        SingleMovie,
        SingleSeries,
    },
    data() {
        return {
            Movies: [],
        };
    },
    methods: {},
    created() { },
};
</script>

<style lang="scss" scoped></style>
