<script setup>
import { ref } from 'vue';
import ItemForm from '../register/itemForm.vue'

const itemFormRef = ref(null)

function showDados() {
    if (itemFormRef.value) {
        console.log(itemFormRef.value.formData)
    }
}

</script>

<template>
    <ItemForm ref="itemFormRef" />
    <button @click="showDados">Ver Dados</button>
</template>