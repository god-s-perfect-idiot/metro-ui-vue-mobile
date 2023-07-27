<template>
    <div class="page">
        <slot></slot>
    </div>
</template>

<style scoped>
.page {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    gap: var(--page-content-gap);
    margin-top: var(--page-content-spacing);
}
</style>