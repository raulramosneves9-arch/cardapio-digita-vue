<script setup>

</script>

<script setup>

</script>

<template>

    <!-- ===== PAGE WRAPPER ===== -->
    <div class="page-wrapper">
        <main class="page-inner">

            <!-- ===== TÍTULO DA PÁGINA ===== -->
            <header class="page-header">
                <span class="page-icon" aria-hidden="true">🍔</span>
                <h1 class="page-title">Cardápio</h1>
                <p class="page-subtitle">Escolha o que você quer administrar</p>
            </header>

            <!-- ===== GRID DE CATEGORIAS ===== -->
            <section class="menu-grid">

                <!-- ===== CATEGORIA: LANCHES ===== -->
                <article class="card" style="display: none;">
                    <header class="card-header">
                        <h2 class="category-title">🍔 Lanches</h2>
                    </header>
                    <ul class="card-body">
                    </ul>
                </article>

                <!-- ===== CATEGORIA: BEBIDAS ===== -->
                <article class="card" style="display: none;">
                    <header class="card-header">
                        <h2 class="category-title">🥤 Bebidas</h2>
                    </header>
                    <ul class="card-body">
                    </ul>
                </article>

                <!-- ===== CATEGORIA: SOBREMESAS ===== -->
                <article class="card" style="display: none;">
                    <header class="card-header">
                        <h2 class="category-title">🍰 Sobremesas</h2>
                    </header>
                    <ul class="card-body">
                    </ul>
                </article>

            </section>
            <!-- fim .menu-grid -->

        </main>
    </div>

</template>

<style scoped>
/* ================================
   IMPORTAÇÃO DE FONTES
   ================================ */
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Nunito:wght@400;600;700;800&display=swap');

/* ================================
   PAGE WRAPPER
   ================================ */
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

/* ================================
   TÍTULO DA PÁGINA
   ================================ */
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

/* ================================
   GRID DE CATEGORIAS
   ================================ */
.menu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
}

/* ================================
   CARD DE CATEGORIA
   ================================ */
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

/* ================================
   HEADER DO CARD (CATEGORIA)
   ================================ */
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

/* ================================
   BODY DO CARD (LISTA DE ITENS)
   ================================ */
.card-body {
    padding: 0.75rem 0;
    margin: 0;
    list-style: none;
}

/* ================================
   ITEM INDIVIDUAL
   ================================ */
.item-card {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.75rem 1.5rem;
    border-bottom: 1px solid #c8760011;
    transition: background 0.15s;
    cursor: pointer;
}

.item-card:last-child {
    border-bottom: none;
}

.item-card:hover {
    background: #2a1a0866;
}

.item-card:hover .item {
    color: #ff9a00;
}

.item-card:hover .item-arrow {
    color: #ff9a00;
    transform: translateX(4px);
}

.item {
    color: #f5deb3;
    font-size: 0.95rem;
    font-weight: 600;
    transition: color 0.15s;
}

.item-arrow {
    color: #6a4a2a;
    font-size: 1.3rem;
    font-weight: 700;
    transition: color 0.15s, transform 0.15s;
}
</style>