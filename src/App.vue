<template>
  <div id="app">
    <div class="title">Welcome to Circuly Internal Tool</div>
    <Home />
  </div>
</template>

<script>
import Home from './views/Home.vue';

export default {
  components: {
    Home
  }
}
</script>

<style lang="scss">
    #app {
    display: flex;
    align-items: center;
    flex-direction: column;
    min-height: 100%;
    background-image: linear-gradient(119deg, #92e361, #12e4ac);
    color: white;
  }
    
  .title {
    margin-top: 1rem;
    text-decoration: none;
    background: white;
    color: #12e4ac;
    padding: 0 1rem;
    border-radius: 2rem;
    font-size: 5rem;
  }
</style>
