<template lang="pug">
div.wrapper
  ThelessonA
  ThelessonB 
  ThelessonC
  ProductList
</template>

<script>
import ThelessonA from './components/ThelessonA'
import ThelessonB from './components/ThelessonB'
import ThelessonC from './components/ThelessonC'
import ProductList from './components/ProductList'

export default {
  name: 'App',
  components: {
    ThelessonA, ThelessonB, ThelessonC,ProductList
  },
  data() {
    return {
      
    }
  },
}
</script>

<style>
.wrapper {
  width: 800px;
  margin: 0 auto;
}
</style>
