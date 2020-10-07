<template>
  <div id="app">
    <Header></Header>
    <Input v-on:emitAdd="addTodoItem"></Input>
    <List v-bind:propsData="todoItems"></List>
    <Footer></Footer>
  </div>
</template>

<script>
  import Header from './components/header'
  import Input from './components/input'
  import List from './components/list'
  import Footer from './components/footer'

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
      addTodoItem: function(item) {
        let obj = {completed: false, item: item};
        localStorage.setItem(item, JSON.stringify(obj));
        this.todoItems.push(obj);
      },
    },
    components: {
      'Header' : Header,
      'Input' : Input,
      'List' : List,
      'Footer' : Footer,
    }

  }
</script>

<style>
  body {
    background-color: #E9F6FD;
  }
</style>
