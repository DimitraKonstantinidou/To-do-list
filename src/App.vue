<template>
  <the-header :title="'To Do List'"></the-header>  
  <do-list></do-list>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import DoList from './components/todolist/Dolist.vue';



export default {
  components: {
    TheHeader,
    DoList,
  }
}
</script>

<style scoped>



@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital@1&display=swap');



html {

  font-family: "Playfair Display", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: italic;
}


</style>