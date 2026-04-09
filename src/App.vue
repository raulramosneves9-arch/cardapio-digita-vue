<script>
import RegisterItem from './views/register/itemForm.vue'
import CreateCard from './views/register/createCard.vue'
import ListItem from './views/list.vue'

export default {
  components: {
    RegisterItem,
    CreateCard,
    ListItem,
  }
}
</script>

<template>
  <RegisterItem />
  <CreateCard />
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