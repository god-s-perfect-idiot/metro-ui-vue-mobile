<script setup lang="ts">
    import { ref } from 'vue'
    import { RouterLink } from 'vue-router';

    const props = defineProps({
        faClass: {
            type: String,
            required: true
        },
        route: {
            type: String,
            required: true
        }
    })
    // classes
    const btn = ref('btn');
</script>

<template>
    <Transition>
        <div :class="btn">
            <RouterLink :to="route">
                <font-awesome-icon :icon="faClass" />
            </RouterLink>
        </div>
    </Transition>
</template>

<style scoped>
    a {
        color: #fff;
    }
    .btn {
        display: flex;
        width: 2rem;
        height: 2rem;
        border-radius: 50%;
        background-color: #1e1e1e;
        border: 2px solid #fff;
        justify-content: center;
        align-items: center;
    }
</style>