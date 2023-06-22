<template>
    <main>
        <SingleMovie />
        <SingleSeries />
    </main>
</template>

<script>

import SingleMovie from "./SingleMovie.vue";
import SingleSeries from "./SingleSeriess.vue";

export default {
    components: {
        SingleMovie,
        SingleSeries,
    },
    data() {
        return {
        };
    },

};
</script>

<style lang="scss" scoped></style>
