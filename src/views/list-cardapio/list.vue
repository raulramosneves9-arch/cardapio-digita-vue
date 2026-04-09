<script setup>
import { computed, ref } from 'vue'

const props = defineProps({ itens: Array })
const emit = defineEmits(['deletarItem'])

const filtroAtivo = ref('todos')

const lanches = computed(() => props.itens.filter(i => i.category === 'lanche'))
const bebidas = computed(() => props.itens.filter(i => i.category === 'bebida'))
const sobremesas = computed(() => props.itens.filter(i => i.category === 'sobremesa'))

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

                <!-- LANCHES -->
                <article class="card" v-show="mostrarLanches">
                    <header class="card-header">
                        <h2 class="category-title">🍔 Lanches</h2>
                    </header>

                    <ul class="card-body">
                        <li class="item-card" :class="{ off: !item.available }" v-for="item in lanches" :key="item.id">

                            <div class="item-info">
                                <span class="item-nome">
                                    <span v-if="!item.available" class="linha"></span>
                                    {{ item.name }}
                                    <span v-if="!item.available" class="linha"></span>
                                </span>

                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>

                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>

                        <li class="item-vazio" v-if="lanches.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

                <!-- BEBIDAS -->
                <article class="card" v-show="mostrarBebidas">
                    <header class="card-header">
                        <h2 class="category-title">🥤 Bebidas</h2>
                    </header>

                    <ul class="card-body">
                        <li class="item-card" :class="{ off: !item.available }" v-for="item in bebidas" :key="item.id">

                            <div class="item-info">
                                <span class="item-nome">
                                    <span v-if="!item.available" class="linha"></span>
                                    {{ item.name }}
                                    <span v-if="!item.available" class="linha"></span>
                                </span>

                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>

                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>

                        <li class="item-vazio" v-if="bebidas.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

                <!-- SOBREMESAS -->
                <article class="card" v-show="mostrarSobremesas">
                    <header class="card-header">
                        <h2 class="category-title">🍰 Sobremesas</h2>
                    </header>

                    <ul class="card-body">
                        <li class="item-card" :class="{ off: !item.available }" v-for="item in sobremesas"
                            :key="item.id">

                            <div class="item-info">
                                <span class="item-nome">
                                    <span v-if="!item.available" class="linha"></span>
                                    {{ item.name }}
                                    <span v-if="!item.available" class="linha"></span>
                                </span>

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

<script setup>
import { computed, ref } from 'vue'

const props = defineProps({ itens: Array })
const emit = defineEmits(['deletarItem'])

const filtroAtivo = ref('todos')

const lanches = computed(() => props.itens.filter(i => i.category === 'lanche'))
const bebidas = computed(() => props.itens.filter(i => i.category === 'bebida'))
const sobremesas = computed(() => props.itens.filter(i => i.category === 'sobremesa'))

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

                <!-- LANCHES -->
                <article class="card" v-show="mostrarLanches">
                    <header class="card-header">
                        <h2 class="category-title">🍔 Lanches</h2>
                    </header>

                    <ul class="card-body">
                        <li class="item-card" :class="{ off: !item.available }" v-for="item in lanches" :key="item.id">

                            <div class="item-info">
                                <span class="item-nome">
                                    <span v-if="!item.available" class="linha"></span>
                                    {{ item.name }}
                                    <span v-if="!item.available" class="linha"></span>
                                </span>

                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>

                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>

                        <li class="item-vazio" v-if="lanches.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

                <!-- BEBIDAS -->
                <article class="card" v-show="mostrarBebidas">
                    <header class="card-header">
                        <h2 class="category-title">🥤 Bebidas</h2>
                    </header>

                    <ul class="card-body">
                        <li class="item-card" :class="{ off: !item.available }" v-for="item in bebidas" :key="item.id">

                            <div class="item-info">
                                <span class="item-nome">
                                    <span v-if="!item.available" class="linha"></span>
                                    {{ item.name }}
                                    <span v-if="!item.available" class="linha"></span>
                                </span>

                                <span class="item-price">R$ {{ item.price }}</span>
                            </div>

                            <button class="btn-delete" @click="emit('deletarItem', item.id)">🗑️</button>
                        </li>

                        <li class="item-vazio" v-if="bebidas.length === 0">Nenhum item cadastrado</li>
                    </ul>
                </article>

                <!-- SOBREMESAS -->
                <article class="card" v-show="mostrarSobremesas">
                    <header class="card-header">
                        <h2 class="category-title">🍰 Sobremesas</h2>
                    </header>

                    <ul class="card-body">
                        <li class="item-card" :class="{ off: !item.available }" v-for="item in sobremesas"
                            :key="item.id">

                            <div class="item-info">
                                <span class="item-nome">
                                    <span v-if="!item.available" class="linha"></span>
                                    {{ item.name }}
                                    <span v-if="!item.available" class="linha"></span>
                                </span>

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

.page-header {
    text-align: center;
}

.page-icon {
    font-size: 3.5rem;
}

.page-title {
    font-size: 3rem;
    color: #ff9a00;
}

.page-subtitle {
    color: #7a5a3a;
    font-size: 0.9rem;
}

.filter-nav {
    display: flex;
    gap: 0.6rem;
    justify-content: center;
    margin-top: 10px;
}

.btn-filter {
    background: transparent;
    border: 1px solid #c8760055;
    border-radius: 999px;
    color: #c87600;
    padding: 0.4rem 1rem;
    cursor: pointer;
}

.btn-filter.active {
    background: #ff9a00;
    color: #1a0a00;
}

.menu-grid {
    display: grid;
    gap: 1.5rem;
}

.card {
    background: #1f1209;
    border-radius: 20px;
    overflow: hidden;
}

.card-header {
    background: linear-gradient(135deg, #c87600, #ff9a00);
    padding: 1rem;
}

.category-title {
    color: #1a0a00;
}

.card-body {
    padding: 0.75rem;
    list-style: none;
}

.item-card {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.7rem 1rem;
    background: #2a1a08;
    border-radius: 10px;
    margin-bottom: 6px;
    transition: 0.2s;
}

.item-card:hover {
    background: #3a2a10;
    transform: translateY(-2px);
}

/* INDISPONÍVEL */
.item-card.off {
    opacity: 0.5;
    filter: grayscale(60%);
}

.item-info {
    display: flex;
    flex-direction: column;
}

.item-nome {
    color: #f5deb3;
    font-weight: 700;
    display: flex;
    align-items: center;
}

.item-price {
    color: #ff9a00;
    font-size: 0.85rem;
}

/* LINHA */
.linha {
    width: 25px;
    height: 1px;
    background: #aaa;
    margin: 0 6px;
}

/* DELETE */
.btn-delete {
    background: transparent;
    border: none;
    cursor: pointer;
}

.item-vazio {
    text-align: center;
    color: #6a4a2a;
}
</style>