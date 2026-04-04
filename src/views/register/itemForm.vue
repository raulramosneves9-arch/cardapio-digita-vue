<script setup>
</script>

<template>
    <h1>Cadastrar Item</h1>
    <span class="inputName">Nome do Item</span>
    <input type="text" placeholder="Ex: X-Burguer">
    <span class="inputName">Preço (R$)</span>
    <input type="text" placeholder="0,00">    
    <span class="inputName">Categoria</span>
    <select name="category">
        <option value="lanche">Lanche</option>
        <option value="bebida">Bebida</option>
        <option value="sobremesa">Sobremesa</option>
    </select>
    <span class="inputName">Disponível</span>
    <input type="checkbox">
</template>

<style scoped>
</style>