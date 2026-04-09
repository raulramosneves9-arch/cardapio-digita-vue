<script setup>
import { ref } from 'vue'
import ItemForm from '../register/itemForm.vue'

const emit = defineEmits(['adicionarItem'])
const itemFormRef = ref(null)

function salvar() {
    if (itemFormRef.value) {
        emit('adicionarItem', { ...itemFormRef.value.formData })
    }
}
</script>

<template>
    <ItemForm ref="itemFormRef" />
    <button @click="salvar">Salvar</button>
</template>