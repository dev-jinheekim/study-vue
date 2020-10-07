<template>
  <div>
      <ul>
          <li v-for="(todoItem, index) in propsData"
              v-bind:key="todoItem"
              v-bind:class="{completed: todoItem.completed}">
              <input type="checkbox" v-on:click="toggleComplete(todoItem)"/>
              {{ todoItem.item }}
              <button v-on:click="deleteItem(todoItem, index)">x</button>
          </li>
      </ul>
  </div>
</template>

<script>
    export default {
        props: ['propsData'],
        methods: {
            deleteItem: function(todoItem, index) {
                console.log(this.todoItems, todoItem, index);
                localStorage.removeItem(todoItem.item);
                this.todoItems.splice(index, 1);
            },
            toggleComplete: function(todoItem) {
                todoItem.completed = !todoItem.completed;
                localStorage.removeItem(todoItem);
                localStorage.setItem(todoItem, JSON.stringify(todoItem));
            }
        }
    }
</script>

<style>
    li {
        list-style: none;
    }
    .completed {
        color: gray;
        text-decoration: line-through;
    }
</style>