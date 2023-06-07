 <!-- // Применение стилей на картинку -->

<template lang="pug">
div   
  h1.title Работа со стилями
    div.puttern(
      
    )
      div.pic_block()
        img(
          v-if="showPic"
          :class="imgFilter"
          :style='[chengedRange, rotatePic]'
          src="../assets/logo.png")
        img(
          v-else
          :class="imgFilter"
           src="../assets/apple.png")
      div
        button(
          
          @click="hendleClick"
          ) Поменяй
        button(
          type="button"
          :class="imgFilter.sepia ? 'active': ''"
          @click="imgFilter.sepia=!imgFilter.sepia"
          ) Сепия
        button(
          type="button"
          @click="imgFilter.whiteBlack=!imgFilter.whiteBlack"
          :class="imgFilter.whiteBlack ? 'active' : ''"          
          ) ЧерноБел 
        form
          h4 Range:
          button(
            type="reset"
           @click="restut"
            )  reset
          .btn-group 
            label Width = {{ imgSizes.currentWidth }}
              input(
                type="range"
                :value="imgSizes.currentWidth"
                @input="imgSizes.currentWidth = $event.target.value"
                :min="imgSizes.minWidth"
                :max="imgSizes.maxWidth"

              ) 
            label Height = {{ imgSizes.currentHeight }}
              input(
                type="range"
                :value="imgSizes.currentHeight"
                @input="checkR"
                :min="imgSizes.minWidth"
                :max="imgSizes.maxWidth"

                )
        form
          h4 Rotate:
          .btn-group 
            label Angle = {{ rotateAngle }} deg
              input(
                type="range"
                :value="rotateAngle"
                @input="rotateAngle = $event.target.value"
                :min='0'
                :max='360'
                ref='name'
              )         




</template>

<script>
export default {
  data() {
    return {
      showPic: true,
      imgFilter: {
        sepia: false,
        whiteBlack: false,
      },

      imgSizes: {
        maxWidth: 480,
        maxHeight: 480,
        currentWidth: 200,
        currentHeight: 300,
        dropW: 500,
        dropH: 500,
      },

      rotateAngle: 0,
    };
  },
  methods: {
    hendleClick() {
      this.showPic = !this.showPic;
    },

   checkR($event){
    console.log($event)
    this.imgSizes.currentHeight = $event.target.value
   },

   restut(){

     console.log(this.$refs.name)
   }
  },

  computed: {
    chengedRange() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`,
      };
    },
    rotatePic(){
      return{
        transform: `rotate(${this.rotateAngle}deg)`
      }
    }
  },
};
</script>

<style scoped>
.title {
  text-align: center;
  color: brown;
}

.puttern {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.pic_block {
  width: 300px;
  height: 500px;
  background-size: contain;
}

img {
  display: block;
  height: 100%;
  width: 100%;
}

.sepia {
  filter: sepia(100%);
}

.whiteBlack {
  filter: grayscale(100%);
}

.active {
  background-color: aqua;
}

button {
  cursor: pointer;
  margin-right: 10px;
}
.btn-group {
  margin-bottom: 20px;
}

input[type="range"] {
  display: block;
}
</style>
