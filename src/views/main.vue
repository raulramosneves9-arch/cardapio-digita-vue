<script setup>
import { ref } from 'vue'
import CreateCard from './register/createCard.vue'
import ListItem from './list-cardapio/list.vue'

const itens = ref([])

function adicionarItem(item) {
    itens.value.push(item)
}
</script>

<template>
    <CreateCard @adicionarItem="adicionarItem" />
    <ListItem :itens="itens" />
</template>