<script setup lang="ts">
    import { ref } from 'vue'
    import PageTitle from './fragments/PageTitle.vue'
    const scrollToView = (element: string) => {
        const el = document.querySelector(element);
        if (el) {
            active.value = element;
            el.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'start' });
        }
    }
    // classes
    const tabs = ref('tabs');
    const tab = ref('tab');
    const active = ref('#tab-one');
    const activeTab = ref('active-tab');
    const passiveTab = ref('passive-tab');
</script>

<template>
    <div :class="tabs">
        <PageTitle :class="[tab, active=='#tab-one' ? activeTab : passiveTab]" text="Main" id="tab-one" @click="scrollToView('#tab-one')"/>
        <PageTitle :class="[tab, active=='#tab-two' ? activeTab : passiveTab]" text="Secondary" id="tab-two" @click="scrollToView('#tab-two')"/>
        <PageTitle :class="[tab, active=='#tab-three' ? activeTab : passiveTab]" text="Teritiary" id="tab-three" @click="scrollToView('#tab-three')"/>
    </div>
</template>

<style scoped>
    .active-tab {
        color: #fff;
    }
    .passive-tab {
        color: #848484;
    }
    .tab {
        scroll-snap-align: start;
    }
    .tab:last-child{
        margin-right: 24rem;
    }
    .tabs {
        display: flex;
        overflow: auto;
        overflow-x: hidden;
        /*overscroll-behavior-x: contain;
        scroll-snap-type: x mandatory;*/
    }
    .tabs::-webkit-scrollbar {
        display: none;
    }

</style>