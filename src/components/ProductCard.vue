<template lang="pug">
.product-card
    img(:src="imgUrl" 
      width="250px"
      height="250px")
    .product-card__info
        h2.title {{ title }}
        p.price {{ price }} $
        p.count {{ count }}
        button( type="button" @click="addToBascked") Добавить в корзину

        

</template>




<script>
export default {
  name: "ProductCard",
  props: {
    title: {
      type: String,
      validator(value) {
        return value.length < 50
      }
    },
    price: {
      type: Number,
      required: true
    },
    imgUrl: {
      type: String,
      default: 'https://tsum.by/images/no-photo.png'
    },
    count: {
      type: Number,
      default: 0
    }
  },

  methods: {
    addToBascked(){
      this.$emit('addToBascked')
    }
  },


}


</script>




<style lang="scss" scoped>
.product-card {
  border: 1px solid rgb(211, 211, 211);
  padding: 20px 15px;
  &__info {
    margin-top: 20px;
    h2, .price .title{
      font-weight: 500;
      font-size: 20px;
    }
    .count {
      color: rgb(143, 143, 143);
    }
    button {
      background-color: rgb(221, 56, 56);
      color: #fff;
      border: none;
      border-radius: 4px;
      padding: 8px 14px;
      display: block;
      cursor: pointer;
      margin-top: 20px;
    }
  }
}
</style>
