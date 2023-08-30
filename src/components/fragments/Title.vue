<script setup lang="ts">
    import { ref } from 'vue'
    const props = defineProps({
        text: {
            type: String,
            required: true
        }
    })
</script>

<template>
    <div class="title">
        <span>{{ props.text }}</span>
    </div>
</template>

<style scoped>
    .title {
        display: flex;
        font-size: 1.5rem;
    }
</style>