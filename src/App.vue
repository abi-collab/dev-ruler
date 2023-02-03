<template>
  <div class="bg-[#87CEEB] border-b border-[#87CEEB] pt-2 z-100">
    <p class="text-md text-right mb-1 flex justify-between md:px-32 xs:px-4"> <p class="text-gray-600 font-bold">Current&nbsp;full&nbsp;width&nbsp;:</p> <p class="text-gray-600 font-bold text-xl">{{ state.width }}&nbsp;<sup>px</sup></p>   </p>
    <div class="flex justify-between font-normal gap-0 text-md w-full">  
      <div class="text-gray-600 xs:block text-right w-full x#87CEEB] sm:bg-white bg-white font-bold pr-2 border-r border-[#87CEEB] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-md text-gray-600 font-bold "> <span v-if="state.width < 640" class="flex"> &#x2190;&nbsp;{{ remaining_width(100) }}px</span></p><p><b class="text-xl sm:text-[#C0C0C0] xs:text-gray-600">xs</b> <small v-if="state.width < 640" class="text-gray-600">(320&nbsp;&#8212;&nbsp;639)</small></p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:block md:block sm:block xs:hidden text-right w-full sm:bg-[#87CEEB] md:bg-white bg-white font-bold pr-2 border-r border-[#87CEEB] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-md"> <span v-if="state.width < 768" class="lg:flex md:flex sm:flex xs:hidden text-gray-600 font-bold"> &#x2190;&nbsp;{{ remaining_width(639) }}px</span></p><p><b class="text-xl md:text-[#C0C0C0] sm:text-gray-600">sm</b> <small v-if="state.width < 768" class="text-gray-600">(640&nbsp;&#8212;&nbsp;767)</small></p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:block md:block sm:hidden xs:hidden text-right w-full md:bg-[#87CEEB] lg:bg-white bg-white font-bold pr-2 border-r border-[#87CEEB] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-md"> <span v-if="state.width < 1024" class="lg:flex md:flex sm:hidden xs:hidden text-gray-600 font-bold"> &#x2190;&nbsp;{{ remaining_width(767) }}px</span></p><p><b class="text-xl lg:text-[#C0C0C0] md:text-gray-600">md</b> <small v-if="state.width < 1024" class="text-gray-600">(768&nbsp;&#8212;&nbsp;1023)</small></p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:block md:hidden sm:hidden xs:hidden text-right w-full lg:bg-[#87CEEB] xl:bg-white bg-white font-bold pr-2 border-r border-[#87CEEB] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-md"> <span v-if="state.width < 1280" class="lg:flex md:hidden sm:hidden xs:hidden text-gray-600 font-bold"> &#x2190;&nbsp;{{ remaining_width(1023) }}px</span></p><p><b class="text-xl xl:text-[#C0C0C0] lg:text-gray-600">lg</b> <small v-if="state.width < 1280" class="text-gray-600">(1024&nbsp;&#8212;&nbsp;1279)</small></p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:hidden md:hidden sm:hidden xs:hidden text-right w-full xl:bg-[#87CEEB] 2xl:bg-white bg-white font-bold pr-2 border-r border-[#87CEEB] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-md"> <span v-if="state.width < 1536" class="lg:flex md:hidden sm:hidden xs:hidden text-gray-600 font-bold"> &#x2190;&nbsp;{{ remaining_width(1279) }}px</span></p><p><b class="text-xl 2xl:text-[#C0C0C0] xl:text-gray-600 ">xl</b> <small v-if="state.width < 1536" class="text-gray-600">(1280&nbsp;&#8212;&nbsp;1535)</small></p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:hidden lg:hidden md:hidden sm:hidden xs:hidden w-full 2xl:bg-[#87CEEB] bg-white font-bold pr-2"> 
        <div class="flex justify-between">
          <p class="mt-auto text-md"> <span class="lg:flex md:hidden sm:hidden xs:hidden text-gray-600 font-bold"> &#x2190;&nbsp;{{ remaining_width(1535) }}&nbsp;<sub>px</sub> </span></p><p><b class="text-xl text-gray-600 ">2xl</b> <small class="text-gray-600">(&gt;&#61;1536)</small></p>
        </div>
      </div>
    </div>
  </div>
</template>
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