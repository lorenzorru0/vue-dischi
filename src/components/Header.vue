<template>
    <header>
        <img :src="logo" alt="Logo app">
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: ['logo']
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variable.scss';

header {
    background-color: $colorBgHeader;
    padding: 1.25rem 1.25rem;

    img {
        width: 4rem;
    }
}
</style>