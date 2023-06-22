<template>
    <header class="d-flex align-items-center justify-content-between px-2">
        <div class="logo-container">
            <img src="../assets/logo.png" alt="Logho di Boolflix">
        </div>
        <SearchBar />
    </header>
</template>

<script>
import SearchBar from "./SearchBar.vue";
export default {
    components: {
        SearchBar,
    },
    data() {
        return {};
    },
};
</script>

<style lang="scss" scoped>
header {
    height: 60px;

    .logo-container {
        padding: .5rem 0;
        height: 100%;

        img {
            height: 100%;
        }
    }
}
</style>
