<template>
  <div
    class="bg-gradient-to-r from-[#7BD3EA] from-20% via-white via-80% to-[#A1EEBD] to-90% border-b border-[#87CEEB] pt-2 z-100 shadow-md">
    <p class="text-md text-right mb-1 flex justify-between md:px-32 xs:px-4">
    <p class="text-gray-900 text-xs sm:flex xs:hidden">Responsive Design Tool (based on Tailwind's media breakpoints)</p>
    <p class="text-gray-600 font-bold text-xs"> <sub>Current&nbsp;full&nbsp;width&nbsp;</sub>{{ state.width
    }}&nbsp;<sub>px</sub></p>
    </p>
    <div class="flex justify-between font-normal gap-0 text-md w-full">
      <!----------------------- XS ------------------------>
      <div class="xs:block text-right w-full sm:bg-none bg-none font-bold pr-1 flex justify-between border-r border-gray-300">
        <div class="flex justify-between">
          <p class="pt-1 text-gray-600 font-bold "> <span v-if="state.width < 640" class="flex font-bold text-xs">
              &nbsp;in&nbsp;{{ remaining_width(100) }}&nbsp;<sub>px</sub></span></p>
          <p><b class="sm:text-xs xs:text-xl sm:text-gray-400 xs:text-gray-600">xs</b> <small v-if="state.width < 640"
              class="text-gray-600">(320&nbsp;&#8212;&nbsp;639)</small></p>
        </div>
      </div>
      <!----------------------- SM ------------------------>
      <div
        class="2xl:block xl:block lg:block md:block sm:block xs:hidden text-right w-full bg-none font-bold pr-1 flex justify-between border-r border-gray-300"> 
        <div class="flex justify-between">
          <p class="pt-1"> <span v-if="state.width < 768"
              class="lg:flex md:flex sm:flex xs:hidden text-gray-600 font-bold text-xs"> &nbsp;in&nbsp;{{
                remaining_width(639) }}&nbsp;<sub>px</sub></span></p>
          <p><b class="md:text-xs sm:text-xl md:text-gray-400 sm:text-gray-600">sm</b> <small v-if="state.width < 768"
              class="text-gray-600">(640&nbsp;&#8212;&nbsp;767)</small></p>
        </div>
      </div>
      <!----------------------- MD ------------------------>
      <div
        class="2xl:block xl:block lg:block md:block sm:hidden xs:hidden text-right w-full bg-none font-bold pr-1 flex justify-between border-r border-gray-300">
        <div class="flex justify-between">
          <p class="pt-1"> <span v-if="state.width < 1024"
              class="lg:flex md:flex sm:hidden xs:hidden text-gray-600 font-bold text-xs"> &nbsp;in&nbsp;{{
                remaining_width(767) }}&nbsp;<sub>px</sub></span></p>
          <p><b class="lg:text-xs md:text-xl lg:text-gray-400 md:text-gray-600">md</b> <small v-if="state.width < 1024"
              class="text-gray-600">(768&nbsp;&#8212;&nbsp;1023)</small></p>
        </div>
      </div>
      <!----------------------- LG ------------------------>
      <div
        class="2xl:block xl:block lg:block md:hidden sm:hidden xs:hidden text-right w-full bg-none font-bold pr-1 flex justify-between border-r border-gray-300">
        <div class="flex justify-between">
          <p class="pt-1"> <span v-if="state.width < 1280"
              class="lg:flex md:hidden sm:hidden xs:hidden text-gray-600 font-bold text-xs"> &nbsp;in&nbsp;{{
                remaining_width(1023) }}&nbsp;<sub>px</sub></span></p>
          <p><b class="xl:text-xs lg:text-xl xl:text-gray-400 lg:text-gray-600">lg</b> <small v-if="state.width < 1280"
              class="text-gray-600">(1024&nbsp;&#8212;&nbsp;1279)</small></p>
        </div>
      </div>
      <!----------------------- XL ------------------------>
      <div
        class="2xl:block xl:block lg:hidden md:hidden sm:hidden xs:hidden text-right w-full bg-none font-bold pr-1 flex justify-between border-r border-gray-300">
        <div class="flex justify-between">
          <p class="pt-1"> <span v-if="state.width < 1536"
              class="lg:flex md:hidden sm:hidden xs:hidden text-gray-600 font-bold text-xs"> &nbsp;in&nbsp;{{
                remaining_width(1279) }}&nbsp;<sub>px</sub></span></p>
          <p><b class="2xl:text-xs xl:text-xl 2xl:text-gray-400 xl:text-gray-600 ">xl</b> <small
              v-if="state.width < 1536" class="text-gray-600">(1280&nbsp;&#8212;&nbsp;1535)</small></p>
        </div>
      </div>
      <!----------------------- 2XL ------------------------>
      <div class="2xl:block xl:hidden lg:hidden md:hidden sm:hidden xs:hidden w-full bg-none font-bold pr-2">
        <div class="flex justify-between">
          <p class="pt-1"> <span class="lg:flex md:hidden sm:hidden xs:hidden text-gray-600 font-bold text-xs my-auto">
              &nbsp;in&nbsp;{{ remaining_width(1535) }}&nbsp;<sub>px</sub> </span></p>
        <p><b class="text-xl text-gray-600 ">2xl</b> <small class="text-gray-600">(1536&nbsp;&#8212;&nbsp;Above)</small>
        </p>
      </div>
    </div>
  </div>
</div></template>
<script setup>
import { reactive, onMounted, onUnmounted } from 'vue';
const state = reactive({
  width: 0
})

function remaining_width(val) {
  return state.width - val;
}

function updateWidth() {
  state.width = window.innerWidth
}

onMounted(() => {
  updateWidth()
  window.addEventListener('resize', updateWidth)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateWidth)
})
</script>