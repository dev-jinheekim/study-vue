<template>
  <div>
      <ul>
          <li v-for="(todoItem, index) in todoItems"
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
        data: function () {
         return {
             todoItems : []
         }
        },
        created: function() {
            let localStorageLength = localStorage.length;
            if (localStorageLength > 0) {
                for (let i = 0; i < localStorageLength; i++ ) {
                    if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
                        console.log(localStorage.getItem(localStorage.key(i)));
                        this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
                    }
                }
            }
        },
        methods: {
            deleteItem: function(todoItem, index) {
                console.log(this.todoItems, todoItem, index);
                localStorage.removeItem(todoItem.item);
                this.todoItems.splice(index, 1);
                // this.todoItems.pop(index);
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