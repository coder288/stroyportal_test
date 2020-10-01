<template>
    <div class="layout">
        <Navbar />
        <Header />
    </div>
</template>

<script>
import Navbar from "./components/Navbar/Navbar";
import Header from "./components/Header/Header";
export default {
    name: 'App',
    components: {
        Navbar, Header
    }
}
</script>

<style lang="scss">
    .layout { width: 1280px; margin: 0 auto; }
</style>
