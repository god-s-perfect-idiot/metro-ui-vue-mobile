<script setup lang="ts">
    import { ref } from 'vue'
    import PageTitle from './fragments/PageTitle.vue'
    import PageContent from './PageContent.vue'
    import TouchEvent from '@/helper-utils/touch-controls';

    const props = defineProps({
        tabs: {
            type: Array as () => {
                text: string,
                id: string
            }[],
            default: () => [],
            required: true
        },
        pages: {
            type: Array as () => string[],
            default: () => [],
            required: true
        }
    })

    const scrollToView = (element: string) => {
        const el = document.querySelector(element);
        if (el) {
            active.value = element;
            el.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'start' });
        }
    }

    const views = props.tabs.map(tab => `#${tab.id}`)
    const pageList = props.pages

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
            // circular navigation
            // viewPointer = (viewPointer + 1) % views.length 
            if (viewPointer + 1 > views.length - 1) {
            } else {
                viewPointer = viewPointer + 1
                scrollToView(views[viewPointer])
                activePage.value = pageList[viewPointer]
            }
        } else if (touchEvent.isSwipeRight()) {
            // circular navigation
            // viewPointer = viewPointer - 1 < 0 ? views.length - 1 : viewPointer - 1
            if(viewPointer - 1 < 0) {
            } else {
                viewPointer = viewPointer - 1
                scrollToView(views[viewPointer])
                activePage.value = pageList[viewPointer]
            }
        }
    }
    document.addEventListener('touchend', handleSwipe);


    // classes
    const tabs = ref('tabs');
    const tabClass = ref('tab');
    const active = ref(views[0]);
    const activePage = ref(pageList[0]);
    const activeTab = ref('active-tab');
    const passiveTab = ref('passive-tab');

</script>

<template>
    <div :class="tabs">
        <PageTitle v-for="tab in props.tabs" :class="[tabClass, active==`#${tab.id}` ? activeTab : passiveTab]" :text="tab.text" :id="tab.id"/>
    </div>
    <div :class="pages">
    </div>
    <TransitionGroup name="waterfall">
        <div v-for="page in props.pages">
            <PageContent v-if="activePage === page">
                <slot :name=page>
                </slot>
            </PageContent>
        </div>
    </TransitionGroup>
</template>

<style scoped>
    
    .active-tab {
        color: #fff;
    }
    .passive-tab {
        color: var(--secondary-color);
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