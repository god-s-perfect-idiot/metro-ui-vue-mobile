<script setup lang="ts">
    import { ref } from 'vue'
    

    const props = defineProps({
        title: {
            type: String,
            required: true,
        },
        description: {
            type: String,
            required: true,
        },
        assignedValue: {
            type: Boolean,
            default: false,
        },
        modelValue: {
            type: Boolean,
            default: false,
        },
        disabled: {
            type: Boolean,
            default: false
        }
    })

    const status = ref(props.assignedValue);
    const emit = defineEmits(['update:modelValue'])

    const toggle = () => {
        status.value = !status.value;
        emit('update:modelValue', status.value)
    }
    
</script>

<template>
    <div v-if="!props.disabled" class="toggle">
        <span class="title">{{ props.title }}</span>
        <div class="status">
            <span class="status-text">{{ status ? 'On' : 'Off' }}</span>
            <div class="status-box on" v-if="status" @click="toggle">
                <div class="status-slider">
                </div>
            </div>
            <div class="status-box off" v-else @click="toggle">
                <div class="status-slider">
                </div>
            </div>
            <!-- <Transition name="slide-right">
                    <div class="off" v-if="status === 'Off'">
                        <div class="status-slider">
                        </div> 
                    </div>
                </Transition>
                <Transition name="slide-left">
                    <div class="on" v-if="status === 'On'">
                        <div class="status-slider">
                        </div>
                    </div>
                </Transition> -->
        </div>
        <span class="description">{{ props.description }}</span>
    </div>
    <div v-else>
        <span class="title">{{ props.title }}</span>
        <div class="status">
            <span class="status-text-disabled">{{ status ? 'On' : 'Off' }}</span>
            <div class="status-box disabled" v-if="status">
                <div class="status-slider">
                </div>
            </div>
            <div class="status-box off" v-else>
                <div class="status-slider">
                </div>
            </div>
        </div>
        <span class="description">{{ props.description }}</span>
    </div>
</template>

<style scoped>
    .toggle {
        display: flex;
        flex-direction: column;
        width: 100%;
    }
    .title {
        color: var(--secondary-color);
    }
    .status {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        margin-top: var(--title-spacing);
    }
    .status-text {
        font-size: 1.8rem;
        font-weight: 200;
    }

    .status-text-disabled {
        font-size: 1.8rem;
        font-weight: 200;
        color: var(--secondary-color)
    }

    .status-box {
        width: 4rem;
        height: 1.5rem;
        border: 2px solid white;
        display: flex;
        align-items: center;
    }

    .off {
        justify-content: flex-start;
        border-left: black;
    }

    .on {
        justify-content: flex-end;
        border-right:black;
        background: var(--accent-color);
    }
    
    .disabled {
        justify-content: flex-end;
        border-right:black;
        background: var(--disabled-color);
    }

    .status-slider {
        width: 1rem;
        height: 2rem;
        background-color: white;
        border: 1px solid black;
    }

    .description {
        font-weight: 200;
        margin-top: 0.6rem;
        color: var(--secondary-color);
    }

</style>