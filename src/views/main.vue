<script setup>
import { ref } from 'vue'
import CreateCard from './register/createCard.vue'
import ListItem from './list-cardapio/list.vue'

const itens = ref(JSON.parse(localStorage.getItem('itens') || '[]'))

function adicionarItem(item) {
    itens.value.push(item)
    localStorage.setItem('itens', JSON.stringify(itens.value))
}
</script>

<template>
    <CreateCard @adicionarItem="adicionarItem" />
    <ListItem :itens="itens" />
</template>