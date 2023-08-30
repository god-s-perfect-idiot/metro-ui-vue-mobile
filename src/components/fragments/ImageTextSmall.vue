<script setup lang="ts">
    import { ref } from 'vue'
    const props = defineProps({
        title: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        imgURL: {
            type: String,
            required: true
        }
    })
</script>

<template>
    <div class="image-description">
        <div class="image-holder">
            <img class="img" :src="props.imgURL" alt="image">
        </div>
        <div class="description">
            <span class="title">{{ props.title }}</span>
            <span class="description-text">{{ props.description }}</span>
        </div>
    </div>
</template>

<style scoped>
    .image-description {
        display: flex;
        flex-direction: row;
        height: 7rem;
    }
    .image-holder {
        display: flex;
    }
    .img {
        height: 7rem;
        width: 7rem;
    }
    .description {
        margin-left: 1rem;
        height: 100%;
        display: flex;
        flex-direction: column;
    }
    .title {
        font-size: 1.3rem;
    }

    .description-text {
        font-size: 1rem;
        font-weight: 200;
        margin-top: 0.5rem;
    }

</style>