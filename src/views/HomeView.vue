<script setup lang="ts">
  import PageView from '../components/PageView.vue';
  import Toggle from '../components/fragments/Toggle.vue';
  import TextBox from '../components/fragments/TextBox.vue';
  import {ref} from 'vue';

  const toggleValue = ref(true);
  const initialTextValue = "Anything"
  const textboxValue = ref(initialTextValue);
  const textboxPageTwoValue = ref(initialTextValue);
//classes
</script>

<template>
  <main class="content">
    <PageView 
      :tabs="[
        {
          text: 'Primary',
          id: 'home-primary'
        },
        {
          text: 'Secondary',
          id: 'home-secondary'
        },
        {
          text: 'Tertiary',
          id: 'home-tertiary'
        }
      ]"
      :pages="[
        'page-one',
        'page-two',
        'page-three'
      ]"
    >
        <template v-slot:page-one>
            <Toggle title="Some Toggle" :description="`This is a toggle. The value is dynamically sent from the parent. Current value is ${toggleValue}`" :assignedValue="true" v-model="toggleValue"/>
            <Toggle title="Disabled Toggle" :description="`This is a disabled toggle.`" :assignedValue="true" :disabled="true"/>
            <TextBox :title="`Dynamic Title ${textboxValue}`" :initialValue="initialTextValue" v-model="textboxValue"/>
            <TextBox title="Disabled Title" :initialValue="initialTextValue" :disabled="true"/>
        </template>
        <template v-slot:page-two>
          <TextBox :title="`Dynamic Title in Page Two ${textboxPageTwoValue}`" :initialValue="initialTextValue" v-model="textboxPageTwoValue"/>    
        </template>
        <template v-slot:page-three>
        </template>
    </PageView>
  </main>
</template>

<style scoped>
  .content {
    margin-left: 0.5rem;
    margin-right: 0.5rem;
  }
</style>
