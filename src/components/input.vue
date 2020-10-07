<template>
  <div>
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="add">
      <button v-on:click="add">add</button>
  </div>
</template>

<script>
    export default {
        data: function () {
            return {
                newTodoItem: ""
            }
        },
        methods: {
            add: function () {
                if (!this.newTodoItem) { return false;}
                this.$emit('emitAdd', this.newTodoItem);
                this.clearInput();
            },
            clearInput: function () {
                this.newTodoItem = '';
            }
        }
    }
</script>

<style scoped>
</style>