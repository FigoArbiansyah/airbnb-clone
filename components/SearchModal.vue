<template>
  <div
    class="fixed left-[50%] -translate-x-[50%] top-4 md:w-[25rem] w-[18rem] py-4 px-5 bg-white rounded-xl z-50 border"
  >
    <div class="grid grid-cols-12 gap-x-2">
      <input
        type="text"
        class="col-span-10 px-3 py-2 outline-none border-b border-white focus:border-gray-300"
        placeholder="Cari barang"
      />
      <button>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="#444"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      </button>
      <button
        class="w-7 h-7 p-1.5 grid place-items-center rounded-full bg-[#ff5a5f] max-md:hidden self-center"
      >
        <img src="~/assets/img/search.svg" alt="" />
      </button>
    </div>
  </div>
</template>
