<script setup>
    import MainNav from '@/Components/MainNav.vue'
    import { ref, provide } from 'vue';
    import { Link } from '@inertiajs/vue3';

    let width = ref('w-[220px]')
    let hide = ref(false)
    const selectedColor = ref('')

    provide('selectedColor', selectedColor);


    function toggleWidth() {
        if(width.value == 'w-[220px]') {
            width.value = 'w-[100px]'
            hide.value = true
        }else {
            width.value = ['w-[220px]']
            hide.value = false
        }
    }
</script>

<template>

<div class="flex min-h-screen">
    <div id="sidebar" class="bg-black p-6 duration-500" :class="[width],
    {
        'bg-red-600' : selectedColor == 'red',
        'bg-blue-600' : selectedColor == 'blue',
        'bg-green-600' : selectedColor == 'green',
    }"
    style="position: relative;">
        <button class="text-xl text-white" @click="toggleWidth" style="position: absolute; right: 10px; top:10px">
            <i class="fa-solid fa-bars"></i>
        </button>
        <div id="branding" :hidden="hide">
            <img src="https://png.pngtree.com/element_pic/00/16/09/2057e0eecf792fb.jpg" alt="Logo"
                class="w-[170px] h-[170px] mx-auto rounded-full object-cover mb-2">


        </div>




        <MainNav :hidden="hide"></MainNav>
        <div class="mt-5" :hidden="hide">
            <label for="colorSelect" class="text-white">Select a color:</label>
                <select v-model="selectedColor" id="colorSelect" @change="updateColor">
                    <option value="red">Red</option>
                    <option value="blue">Blue</option>
                    <option value="green">Green</option>
                </select>
            </div>
        </div>
    <div id="container" class="flex-1">
        <slot />
    </div>
</div>

</template>
