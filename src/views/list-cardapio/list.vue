<script setup>
import { computed, ref } from 'vue'

const props = defineProps({ itens: Array })
const emit = defineEmits(['deletarItem'])

const filtroAtivo = ref('todos')

const lanches = computed(() => props.itens.filter(i => i.category === 'lanche' && i.available))
const bebidas = computed(() => props.itens.filter(i => i.category === 'bebida' && i.available))
const sobremesas = computed(() => props.itens.filter(i => i.category === 'sobremesa' && i.available))

const mostrarLanches = computed(() => filtroAtivo.value === 'todos' || filtroAtivo.value === 'lanches')
const mostrarBebidas = computed(() => filtroAtivo.value === 'todos' || filtroAtivo.value === 'bebidas')
const mostrarSobremesas = computed(() => filtroAtivo.value === 'todos' || filtroAtivo.value === 'sobremesas')
</script>

<template>
    <div class="page-wrapper">
        <main class="page-inner">
            <header class="page-header">
                <span class="page-icon">🍔</span>
                <h1 class="page-title">Cardápio</h1>
                <p class="page-subtitle">Escolha o que você quer administrar</p>
                <nav class="filter-nav">
                    <button :class="['btn-filter', { active: filtroAtivo === 'todos' }]"
                        @click="filtroAtivo = 'todos'">Todos</button>
                    <button :class="['btn-filter', { active: filtroAtivo === 'lanches' }]"
                        @click="filtroAtivo = 'lanches'">Lanches</button>
                    <button :class="['btn-filter', { active: filtroAtivo === 'bebidas' }]"
                        @click="filtroAtivo = 'bebidas'">Bebidas</button>
                    <button :class="['btn-filter', { active: filtroAtivo === 'sobremesas' }]"
                        @click="filtroAtivo = 'sobremesas'">Sobremesas</button>
                </nav>
            </header>

            <section class="menu-grid">

                <article class="card" v-show="mostrarLanches">
                    <header class="card-header">
                        <h2 class="category-title">🍔 Lanches</h2>
                    </header>
                    <ul class="card-body">
                        <li class="item-card" v-for="item in lanches" :key="item.id">
                            <div class="item-info">
                                <span class="item-nome">{{ item.name }}</span>
                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>
                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>
                        <li class="item-vazio" v-if="lanches.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

                <article class="card" v-show="mostrarBebidas">
                    <header class="card-header">
                        <h2 class="category-title">🥤 Bebidas</h2>
                    </header>
                    <ul class="card-body">
                        <li class="item-card" v-for="item in bebidas" :key="item.id">
                            <div class="item-info">
                                <span class="item-nome">{{ item.name }}</span>
                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>
                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>
                        <li class="item-vazio" v-if="bebidas.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

                <article class="card" v-show="mostrarSobremesas">
                    <header class="card-header">
                        <h2 class="category-title">🍰 Sobremesas</h2>
                    </header>
                    <ul class="card-body">
                        <li class="item-card" v-for="item in sobremesas" :key="item.id">
                            <div class="item-info">
                                <span class="item-nome">{{ item.name }}</span>
                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>
                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>
                        <li class="item-vazio" v-if="sobremesas.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

            </section>
        </main>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Nunito:wght@400;600;700;800&display=swap');

.page-wrapper {
    min-height: 50vh;
    background-color: #1a1008;
    background-image:
        radial-gradient(ellipse at bottom left, #3d1f00 0%, transparent 50%),
        radial-gradient(ellipse at top right, #2a0f00 0%, transparent 50%);
    display: flex;
    justify-content: center;
    font-family: 'Nunito', sans-serif;
    padding: 3rem 1.5rem;
}

.page-inner {
    width: 100%;
    max-width: 860px;
    display: flex;
    flex-direction: column;
    gap: 2.5rem;
}

.filter-nav {
    display: flex;
    gap: 0.6rem;
    flex-wrap: wrap;
    justify-content: center;
}

.btn-filter {
    background: transparent;
    border: 1px solid #c8760055;
    border-radius: 999px;
    color: #c87600;
    font-family: 'Nunito', sans-serif;
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 1px;
    padding: 0.45rem 1.1rem;
    cursor: pointer;
    transition: background 0.2s, color 0.2s, border-color 0.2s;
}

.btn-filter:hover {
    background: #c87600;
    color: #1a0a00;
    border-color: #c87600;
}

.btn-filter.active {
    background: #ff9a00;
    color: #1a0a00;
    border-color: #ff9a00;
}

.page-header {
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
}

.page-icon {
    font-size: 3.5rem;
    filter: drop-shadow(0 4px 12px rgba(0, 0, 0, 0.4));
}

.page-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3rem;
    color: #ff9a00;
    letter-spacing: 4px;
    margin: 0;
    line-height: 1;
}

.page-subtitle {
    color: #7a5a3a;
    font-size: 0.9rem;
    font-weight: 600;
    margin: 0;
    letter-spacing: 1px;
    text-transform: uppercase;
}

.menu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
}

.card {
    background: #1f1209;
    border: 1px solid #c8760033;
    border-radius: 20px;
    overflow: hidden;
    box-shadow:
        0 20px 50px rgba(0, 0, 0, 0.5),
        0 0 0 1px #c8760011;
    transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
    transform: translateY(-4px);
    box-shadow:
        0 28px 60px rgba(0, 0, 0, 0.6),
        0 0 0 1px #c8760033;
}

.card-header {
    background: linear-gradient(135deg, #c87600, #ff9a00);
    padding: 1rem 1.5rem;
}

.category-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem;
    color: #1a0a00;
    letter-spacing: 2px;
    margin: 0;
}

.card-body {
    padding: 0.75rem;
    margin: 0;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.item-card {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.75rem 1rem;
    background: #2a1a08;
    border: 1px solid #c8760022;
    border-radius: 12px;
    transition: background 0.15s, border-color 0.15s;
}

.item-card:hover {
    background: #3a2a10;
    border-color: #c8760055;
}

.item-info {
    display: flex;
    flex-direction: column;
    gap: 0.2rem;
}

.item-nome {
    color: #f5deb3;
    font-size: 0.95rem;
    font-weight: 700;
}

.item-price {
    color: #ff9a00;
    font-weight: 700;
    font-size: 0.85rem;
}

.btn-delete {
    background: transparent;
    border: 1px solid #ff000033;
    border-radius: 8px;
    padding: 0.4rem 0.6rem;
    cursor: pointer;
    font-size: 1rem;
    transition: background 0.2s, border-color 0.2s;
}

.btn-delete:hover {
    background: #ff000033;
    border-color: #ff000066;
}

.item-vazio {
    padding: 1rem;
    color: #6a4a2a;
    font-size: 0.85rem;
    font-style: italic;
    text-align: center;
}
</style>