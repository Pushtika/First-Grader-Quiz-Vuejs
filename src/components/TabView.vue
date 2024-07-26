<template>
  <div class="q-pa-md">
    <div class="q-gutter-y-md" style="max-width: 100vw">
      <q-tabs
      v-model="tab"
      dense
      class="text-grey tab"
      active-color="white"
      indicator-color="white"
      align="justify"
      narrow-indicator
      >
      <q-tab v-for="quiz in quizes" :key="quiz.id" :name="quiz.subject" :label="quiz.subject" />
      <q-separator />
    </q-tabs>
    
    <q-tab-panels v-model="tab" animated>
      <q-tab-panel v-for="quiz in quizes" :key="quiz.id" :name="quiz.subject">
        <Categories :quiz="quiz" />
      </q-tab-panel>
    </q-tab-panels>
  </div>
</div>
</template>

<script setup>
import english from '../data/English.json';
import math from '../data/Math.json';
import french from '../data/French.json';
import { ref, onMounted } from 'vue';
import Categories from './Categories.vue';

const mergedData = [
{ id: math.id, subject: math.subject, categories: math.categories },
{ id: english.id, subject: english.subject, categories: english.categories },
{ id: french.id, subject: french.subject, categories: french.categories },
];
const quizes = ref(mergedData);

const tab = ref('');

onMounted(() => {
  if (quizes.value.length > 0) {
    tab.value = quizes.value[0].subject;
  }
});

</script>

<style scoped>
.tab{
  background-color: #FA1E44;
}

.q-tab-panels{
  background-color: #5AB190;
}

</style>