<template>
    <div class="alerta">
        <slot></slot>
    </div>
</template>

<style scoped>
    .alerta {
        padding: 1rem;
        font-weight: 900;
        text-transform: uppercase;
        font-size: 1.6rem;
        text-align: center;
        background-color: var(--white);
        border-left: .9rem solid #B91C1C;
        border-top: .1rem solid #B91C1C;
        border-bottom: .1rem solid #B91C1C;
        border-right: .1rem solid #B91C1C;
        color: #B91C1C;
        margin-bottom: 3rem;
    }
</style>