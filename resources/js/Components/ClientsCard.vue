<template>
    <div class="bg-gray-400 shadow-md p-2 rounded-lg mx-2">
        <div class="flex justify-center mb-2">
  <img
    src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSIvS4mcVtc7bXTAsvtZJFaEjKbxUiAI4_l5Dh0xBZA7GEQGWnQ0Q1TIEfVqWcl4R4wioA&usqp=CAU"
    alt="logo"
    class="logo-image"
  >
</div>

      <h3 class="text-sm font-semibold">{{ client.last_name }}, {{ client.first_name }}</h3>
      <p class="text-gray-700 text-xs">{{ client.address }}</p>
      <span class="card-level mt-2 bg-green-500 text-white px-2 py-1 rounded text-xs">
          Level {{ client.level }}
        </span>
      <button class="border-2 border-solid rounded-md border-gray-700
      p-2 ml-3"
      :class="{
            'bg-red-600' : selectedColor == 'red',
            'bg-blue-600' : selectedColor == 'blue',
            'bg-green-600' : selectedColor == 'green',
            }"
      >Click Me</button>
    </div>
  </template>

<script setup>
import { defineProps } from 'vue';
import { inject } from 'vue';

const selectedColor = inject('selectedColor')
// const selectedColor = ref('')

const props = defineProps({
  client: Object,
});
</script>

