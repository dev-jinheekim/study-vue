<template>
    <button v-on:click="deleteAll">clear all</button>
</template>

<script>
    export default {
        methods: {
            deleteAll: () => {
                localStorage.clear();
            }
        }
    }
</script>

<style>
</style>