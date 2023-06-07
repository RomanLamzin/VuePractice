<!-- // разбор работы слота -->

<template lang="pug" >
div
    slot 
    button(
        type="button"
        ref="newModel"
        @click="testCon"
    ) TEST B
</template>

<script>

export default {
    methods: {
        testCon(){
            console.log(this.$refs.newModel.innerHTML="вот эт да")
        }
    },
}
</script>
