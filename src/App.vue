<script>
import RegisterItem from './views/register/itemForm.vue'
import ListItem from './views/list-cadapio/list.vue'

export default {
  components: {
    RegisterItem,
    ListItem
  }
}
</script>

<template>
  <RegisterItem />
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