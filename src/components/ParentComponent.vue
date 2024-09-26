<template>
    <div>
      <h2>Slider 1</h2>
      <SliderComponent v-model="sliderValue1" />
  
      <h2>Slider 2</h2>
      <SliderComponent v-model="sliderValue2" />
  
      <p>Wert Slider 1: {{ sliderValue1 }}</p>
      <p>Wert Slider 2: {{ sliderValue2 }}</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, watch } from 'vue';
  import SliderComponent from './SliderComponent.vue';
  
  // Reaktive Werte für die Slider
  const sliderValue1 = ref(50);
  const sliderValue2 = ref(50);
  
  // Synchronisieren der Werte zwischen den Slidern
  watch(sliderValue1, (newValue) => {
    sliderValue2.value = newValue;
  });
  
  // Optional: Synchronisation in beide Richtungen
  watch(sliderValue2, (newValue) => {
    sliderValue1.value = newValue;
  });
  </script>