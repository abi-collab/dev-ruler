<template>
  <div class="bg-[#44A08D] border-b border-[#44A08D] pt-2 z-100">
    <p class="text-md text-center mb-1 text-white font-bold">Current full width: {{ state.width }} <sup>px</sup> </p>
    <div class="flex justify-between font-normal gap-0 text-md w-full">  
      <div class="text-gray-600 xs:block text-right w-full xs:bg-[#44A08D] sm:bg-white bg-white font-bold pr-2 border-r border-[#44A08D] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-xs"> <span class="flex"> &#x2190; {{ remaining_width(319) }}px</span></p><p><b class="text-xl text-black">xs</b> (320-639)</p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:block md:block sm:block xs:hidden text-right w-full sm:bg-[#44A08D] md:bg-white bg-white font-bold pr-2 border-r border-[#44A08D] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-xs"> <span class="lg:flex md:flex sm:flex xs:hidden"> &#x2190; {{ remaining_width(639) }}px</span></p><p><b class="text-xl text-black">sm</b> (640-767)</p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:block md:block sm:hidden xs:hidden text-right w-full md:bg-[#44A08D] lg:bg-white bg-white font-bold pr-2 border-r border-[#44A08D] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-xs"> <span class="lg:flex md:flex sm:hidden xs:hidden"> &#x2190; {{ remaining_width(767) }}px</span></p><p><b class="text-xl text-black">md</b> (768-1023)</p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:block md:hidden sm:hidden xs:hidden text-right w-full lg:bg-[#44A08D] xl:bg-white bg-white font-bold pr-2 border-r border-[#44A08D] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-xs"> <span class="lg:flex md:hidden sm:hidden xs:hidden"> &#x2190; {{ remaining_width(1023) }}px</span></p><p><b class="text-xl text-black">lg</b> (1024-1279)</p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:block lg:hidden md:hidden sm:hidden xs:hidden text-right w-full xl:bg-[#44A08D] 2xl:bg-white bg-white font-bold pr-2 border-r border-[#44A08D] flex justify-between">
        <div class="flex justify-between">
          <p class="mt-auto text-xs"> <span class="lg:flex md:hidden sm:hidden xs:hidden"> &#x2190; {{ remaining_width(1279) }}px</span></p><p><b class="text-xl text-black">xl</b> (1280-1535)</p>
        </div>
      </div>
      <div class="text-gray-600 2xl:block xl:hidden lg:hidden md:hidden sm:hidden xs:hidden w-full 2xl:bg-[#44A08D] bg-white font-bold pr-2"> 
        <div class="flex justify-between">
          <p class="mt-auto text-xs"> <span class="lg:flex md:hidden sm:hidden xs:hidden"> &#x2190; {{ remaining_width(1535) }}px</span></p><p><b class="text-xl text-black">2xl</b> (>=1536)</p>
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