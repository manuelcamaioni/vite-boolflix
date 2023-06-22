<template>
    <main>
        <div class="px-2">
            <SingleMovie />
        </div>
        <div class="px-2">
            <SingleSeries />
        </div>

    </main>
</template>

<script>

import SingleMovie from "./SingleMovie.vue";
import SingleSeries from "./SingleSeries.vue";

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
