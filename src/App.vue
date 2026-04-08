<script>
import RegisterItem from './views/register/itemForm.vue'
import ListItem from './views/list.vue'
import createCard from './views/register/createCard.vue';

export default {
  components: {
    RegisterItem,
    createCard,
    ListItem,

  }
}
</script>

<template>
  <RegisterItem />
  <createCard />
  <ListItem />
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
  width: 100%;
}
</style>