<template>
    <input
      type="range"
      :min="min"
      :max="max"
      :step="step"
      v-model="internalValue"
    />
  </template>
  
  <script lang="ts">
  import { defineComponent, ref, watch } from 'vue';
  
  export default defineComponent({
    name: 'SliderComponent',
    props: {
      modelValue: {
        type: Number,
        default: 0,
      },
      min: {
        type: Number,
        default: 0,
      },
      max: {
        type: Number,
        default: 100,
      },
      step: {
        type: Number,
        default: 1,
      },
    },
    emits: ['update:modelValue'],
    setup(props, { emit }) {
      const internalValue = ref(props.modelValue);
  
      watch(
        () => props.modelValue,
        (newVal) => {
          internalValue.value = newVal;
        }
      );
  
      watch(internalValue, (newVal) => {
        emit('update:modelValue', newVal);
      });
  
      return {
        internalValue,
      };
    },
  });
  </script>