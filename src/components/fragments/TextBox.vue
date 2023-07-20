<script setup lang="ts">
    import { ref } from 'vue'
    const props = defineProps({
        title: {
            type: String,
            required: true
        },
        initialValue: {
            type: String,
            required: false,
            default: ""
        },
        modelValue: {
            type: String,
            default: '',
        },
        disabled: {
            type: Boolean,
            default: false
        }
    })
    const textContent = ref(props.initialValue);
    const emit = defineEmits(['update:modelValue'])
    const emitEdit = (e: any) => {
        textContent.value = e.target?.value;
        emit('update:modelValue', e.target?.value)
    }
</script>


<template>
    <div v-if="!props.disabled">
        <span class="title">
            {{ props.title }}
        </span>
        <div class="text">
            <input type="text" :value="textContent" @input="e => emitEdit(e)"/>
        </div>
    </div>
    <div v-else>
        <span class="title">
            {{ props.title }}
        </span>
        <div class="disabled">
            <input type="text" :value="textContent" disabled/>
        </div>
    </div>
</template>

<style scoped>
    .title {
        color: var(--secondary-color)
    }
    .text {
        display: flex;
        width: 100%;
    }
    .text input {
        margin-top: var(--title-spacing);
        background-color: var(--grey-fill-color);
        height: 2rem;
        width: 100%;
        font-size: 1.1rem;
        padding-left: 0.5rem;
    }
    .disabled {
        width: 100%;
        display: flex;
    }
    .disabled input {
        margin-top: var(--title-spacing);
        background-color: black;
        color: var(--secondary-color);
        border: 2px var(--secondary-color) solid;
        height: 2rem;
        width: 100%;
        font-size: 1.1rem;
        padding-left: 0.5rem;
    }
</style>