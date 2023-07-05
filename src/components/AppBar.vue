
<script setup lang="ts">
    import OvalButton from './fragments/OvalButton.vue'
    import { ref } from 'vue'

    const props = defineProps({
        iconButtons: {
            type: Array as () => {
                title: string,
                route: string
            }[],
            required: false
        },
    })
    let expanded = ref(false);

    const toggleAppbar = () => {
        expanded.value = !expanded.value;
    }

    // classes
    const appBar = ref('app-bar');
    const collapsed = ref('collapsed');
    const barExpanded = ref('expanded');
    const barLauncher = ref('bar-launcher');
    const appBtns = ref('app-btns');

</script>

<template>
    <Transition name="appbar-enter">
        <div v-if="!expanded" :class="[appBar, collapsed]">
            <div :class="barLauncher" @click="toggleAppbar()">
                <div></div>
                <div></div>
                <div></div>
            </div>
        </div>
    </Transition>
    <Transition name="appbar-exit">
        <div v-if="expanded" :class="[appBar, barExpanded]">
            <div :class="appBtns">
                <div v-for="(iconButton) in iconButtons">
                    <OvalButton :faClass="iconButton.title" :route="iconButton.route"/>
                </div>
            </div>
            <div :class="barLauncher" @click="toggleAppbar()">
                <div></div>
                <div></div>
                <div></div>
            </div>
        </div>
    </Transition>
</template>

<style scoped>
    .app-btns {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-left: 2rem;
        width: 100%;
        gap: 2rem;
        flex-direction: row;
    }
    .collapsed {
        height: 4rem;
        margin-bottom: -2rem;
    }
    .expanded {
        height: 4rem;
    }
    .app-bar {
        background-color: #1e1e1e;
        position: fixed;
        bottom: 0;
        left: 0;
        display: flex;
        width: 100%;
        justify-content: flex-end;
    }
    .bar-launcher {
        display: flex;
        top: 0;
        padding-right: 0.7rem;
        padding-top: 0.7rem;
        font-size: 1.4rem;
        font-weight: bolder;
        font-family: as;
        gap: 0.3rem;
    }
    .bar-launcher > div {
        height: 0.3rem;
        width: 0.3rem;
        background-color: #fff;
        border-radius: 50%;
    }
</style>