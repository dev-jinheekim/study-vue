<template>
  <div>
      <ul>
          <li v-for="(todoItem, index) in propsData"
              v-bind:key="todoItem"
              v-bind:class="{completed: todoItem.completed}">
              <input type="checkbox" v-on:click="toggleComplete(todoItem)"/>
              {{ todoItem.name }}
              <button v-on:click="remove(todoItem, index)">x</button>
          </li>
      </ul>
  </div>
</template>

<script>
    export default {
        props: ['propsData'],
        methods: {
            remove: function (todoItem, index) {
                this.$emit('emitRemove', todoItem, index);
            },
            toggleComplete: function (todoItem) {
                this.$emit('emitToggleComplete', todoItem);
            }
        }
    }
</script>

<style>
    ul {
        padding: 0;
    }
    li {
        list-style: none;
    }
    .completed {
        color: gray;
        text-decoration: line-through;
    }
</style>