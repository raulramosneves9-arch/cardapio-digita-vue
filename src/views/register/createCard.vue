<script setup>
import { reactive, ref } from 'vue';
import ItemForm from './itemForm.vue'

const itemFormRef = ref(null)

</script>

<template>
    <ItemForm ref="itemFormRef" />
</template>