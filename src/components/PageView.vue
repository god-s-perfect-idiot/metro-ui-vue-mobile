<script setup lang="ts">
    import { ref } from 'vue'
    import PageTitle from './fragments/PageTitle.vue'
    import TouchEvent from '@/helper-utils/touch-controls';
    const scrollToView = (element: string) => {
        const el = document.querySelector(element);
        if (el) {
            active.value = element;
            el.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'start' });
        }
    }

    const views = ["#tab-one", '#tab-two', "#tab-three"]
    let viewPointer = 0;
    let touchEvent:any = null
    document.addEventListener('touchstart', (event: any) => {
        touchEvent = new TouchEvent(event)
    })
    const handleSwipe = (event: any) => {
        if (!touchEvent) {
            return
        }
        touchEvent.setEndEvent(event);
        if (touchEvent.isSwipeLeft()) {
            // viewPointer = (viewPointer + 1) % views.length 
            if (viewPointer + 1 > views.length - 1) {
            } else {
                viewPointer = viewPointer + 1
                scrollToView(views[viewPointer])
            }
        } else if (touchEvent.isSwipeRight()) {
            // viewPointer = viewPointer - 1 < 0 ? views.length - 1 : viewPointer - 1
            if(viewPointer - 1 < 0) {
            } else {
                viewPointer = viewPointer - 1
                scrollToView(views[viewPointer])
            }
        }
    }
    document.addEventListener('touchend', handleSwipe);


    // classes
    const tabs = ref('tabs');
    const tab = ref('tab');
    const active = ref('#tab-one');
    const activeTab = ref('active-tab');
    const passiveTab = ref('passive-tab');


</script>

<template>
    <div :class="tabs">
        <PageTitle :class="[tab, active=='#tab-one' ? activeTab : passiveTab]" text="Main" id="tab-one"/>
        <PageTitle :class="[tab, active=='#tab-two' ? activeTab : passiveTab]" text="Secondary" id="tab-two" />
        <PageTitle :class="[tab, active=='#tab-three' ? activeTab : passiveTab]" text="Teritiary" id="tab-three"/>
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