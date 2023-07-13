<script setup lang="ts">
    import { ref } from 'vue'
    const props = defineProps({
        text: {
            type: String,
            required: true
        }
    })
    // classes
    const pageTitle = ref('page-title');
</script>

<template>
    <div :class="pageTitle">
        {{ props.text }}
    </div>
</template>

<style scoped>
    .page-title {
        display: flex;
        font-size: 3rem;
        justify-content: flex-start;
        text-transform: lowercase;
        font-weight:200;
        margin-right: 1rem;
    }
</style>