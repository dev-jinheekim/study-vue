<template>
  <div id="app">
    <Header></Header>
    <Input></Input>
    <List></List>
    <Footer></Footer>
  </div>
</template>

<script>
  import Header from './components/header'
  import Input from './components/input'
  import List from './components/list'
  import Footer from './components/footer'

  export default {

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
