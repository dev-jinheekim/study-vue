<template>
  <div>
      <ul>
          <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem">
              <input type="checkbox" v-on:click="toggleComplete"/>
              {{ todoItem }}
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
                        this.todoItems.push(localStorage.key(i));
                    }
                }
            }
        },
        methods: {
            deleteItem: function(todoItem, index) {
                console.log(this.todoItems, todoItem, index);
                localStorage.removeItem(todoItem);
                this.todoItems.splice(index, 1);
                // this.todoItems.pop(index);
            },
            toggleComplete: function() {

            }
        }
    }
</script>

<style>
    li {
        list-style: none;
    }
</style>