<template>
  <div id="app">
    <BotList />
  </div>
</template>

<script>
  import BotList from './components/BotList';

  export default {
    name: 'App',

    components: {
      BotList
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    background-color: #19191a;
    color: whitesmoke;
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  h1, h2, h3 {
    margin: 0;
  }

  button {
    cursor: pointer;
  }

  #app {
    display: flex;
    justify-content: center;
    font-family: Arial,Helvetica,sans-serif
  }
</style>
