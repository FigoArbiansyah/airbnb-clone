<template>
  <div class="mt-3 flex justify-center">
    <div class="py-4 px-3 border rounded-xl flex items-center">
      <p class="font-semibold pr-4 border-r border-gray-300">
        Tampilkan harga total
      </p>
      <p class="text-gray-500 pl-4">Termasuk semua biaya, sebelum pajak</p>
      <div
        class="ml-6 w-14 h-8 rounded-full bg-gray-400 bg-opacity-80 p-[1px] relative hover:bg-[#717171] cursor-pointer transition-all ease duration-300"
        @click="toggle()"
      >
        <div
          class="absolute top-[2px] left-[2px] w-7 h-7 bg-white rounded-full switch-button transition-all ease duration-300"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup>
const toggle = () => {
  document.querySelector(".switch-button").classList.toggle("left-[2px]");
  document.querySelector(".switch-button").classList.toggle("right-[2px]");
};
</script>

<style setup>
.switch-button {
  transition: all 0.3s ease;
}
</style>
