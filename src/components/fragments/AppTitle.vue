<script setup lang="ts">
    import { ref } from 'vue'
    const props = defineProps({
        text: {
            type: String,
            required: true
        }
    })
    // classes
    const appTitle = ref('app-title');
</script>

<template>
    <div :class="appTitle">
        {{ props.text }}
    </div>
</template>

<style scoped>
    .app-title {
        display: flex;
        text-align: center;
        font-size: 0.9rem;
        justify-content: flex-start;
        text-transform: uppercase;
        font-weight:600;
        color: #fff;
        padding: 0.5rem;
    }
</style>