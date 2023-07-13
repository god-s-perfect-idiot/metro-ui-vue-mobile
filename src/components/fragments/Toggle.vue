<script setup lang="ts">
    import { ref } from 'vue'
    
    const status = ref('Off');

    const toggle = () => {
        if (status.value === 'Off') {
            status.value = 'On'
        } else {
            status.value = 'Off'
        }
    }

</script>

<template>
    <div class="toggle">
        <span class="title">The Toggle Title</span>
        <div class="status">
            <span class="status-text">{{ status }}</span>
            <div class="status-box on" v-if="status === 'On'" @click="toggle">
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
        <span class="description">Click the Toggle to change the status</span>
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
        margin-top: 0.3rem;
    }
    .status-text {
        font-size: 1.8rem;
        font-weight: 200;
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