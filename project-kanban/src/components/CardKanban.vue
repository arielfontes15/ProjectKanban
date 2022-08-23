<template>
    <div class="card">
        <slot />
    </div>
</template>

<script>
export default {
    name: "CardKanban"
}
</script>

<style scoped>
.card{
    background: #f0f0f0;
    padding: 1.4rem;
    border-radius: 0.4rem;
    box-shadow: 0 1px 0 rgba(9, 30, 66, 0.25);
    margin-bottom: 0.8rem;
    font-size: 1.6rem;
    cursor: pointer;
}
</style>