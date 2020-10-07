<template>
    <button v-on:click="deleteAll">clear all</button>
</template>

<script>
    export default {
        methods: {
            deleteAll: function () {
                this.$emit('emitRemoveAll');
            }
        }
    }
</script>

<style>
</style>