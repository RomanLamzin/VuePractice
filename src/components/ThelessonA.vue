<!-- // перебор по кол-ву -->

<template lang="pug">
h1 Выбери кол-во продуктов
    hr
    button(
        type="button"
        @click="decCount"
        ) -
    input(
        type="text"
        :value="currentNumber"
      

         )
    button(
        type="button"
        @click="addCount"
        ) +

</template>

<script>
export default {
  data() {
    return {
      currentNumber: 0,
      maxCount:10,
      minCount:1,
    };
  },
  methods: {
    addCount() {
     if(this.currentNumber<this.maxCount)
        this.currentNumber++;
      
    },

    decCount() {
        if(this.currentNumber>this.minCount)
        this.currentNumber--;
      
    },
  },
};
</script>

<style  scoped>

button,
input {
    display: inline-block;
}
</style>
