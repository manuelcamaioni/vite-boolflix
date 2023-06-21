<template>
    <div>
        <ul>
            <li v-for="movie in store.MoviesList">
                <span>{{ movie.title }}</span>
                <span>{{ movie.original_title }}</span>
                <span>{{ movie.original_language }}</span>
                <span>{{ movie.vote_average }}</span>
            </li>
        </ul>
    </div>
</template>

<script>
import { store } from "../store";
export default {
    props: {
        Movies: Array,
    },

    data() {
        return {
            store,
        };
    },
};
</script>

<style lang="scss" scoped></style>
