<template lang="pug">
div.flex
    input( 
    type="text"
    @input="$emit('input', $event.target.value)"
    ) 
    button(
        type="button"
        @click="findProduct") Find
</template>

<script>
export default {
  model: {
    prop: 'value',
    event: 'input'
  },

  methods: {
    findProduct(){
        this.$emit("findProduct")
    }

  },


}
</script>

<style lang="scss" scoped>
input {
  height: 25px;
  margin-left: 40px;
  margin-right: 20px;
}
.flex {
    display: flex;
    align-items: center;
    justify-content: center;
}
button {
      background-color: rgb(221, 56, 56);
      color: #fff;
      border: none;
      border-radius: 4px;
      padding: 8px 14px;
      display: block;
      cursor: pointer;
      
    }

</style>
