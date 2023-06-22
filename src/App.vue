<template>
    <AppHeader />
    <AppMain />
</template>

<script>
// 256550ff1fdca66f331fdd0d6cec4eef API KEY
import AppMain from "./components/AppMain.vue";
import AppHeader from "./components/AppHeader.vue";
export default {
    components: {
        AppMain,
        AppHeader,
    },
    data() {
        return {};
    },
};
</script>

<style lang="scss">
@import "bootstrap/scss/bootstrap";
@import "./styles/general.scss";
</style>
