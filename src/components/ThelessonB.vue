<!-- // Поиск по буквам -->


<template lang="pug">
h1 Поисковик по буквам!
    hr
    input( 
        type="text"
        v-model="letter"
        )
    <p>Всего имен: {{ users.length }}, совпадений: {{ getFilteredNames.length }}</p>
    hr
    ol
        li(v-for="user in getFilteredNames") {{ user }}

</template>

<script>
export default {
  data() {
    return {
      users: ['Данил', 'Василий', 'Дмитрий', 'Григорий', 'Максим'],
      letter:''
    };
  },

  computed: {
    getFilteredNames() {
      return this.users.filter(name => name.toLowerCase().includes(this.letter.toLowerCase()))
    }

  },

};
</script>

<style scoped></style>
