<template>
  
    <nav class="py-4 md:px-[35px] px-3 border-y border-gray-200">
      <div class="flex justify-between max-md:gap-x-2">
        <NuxtLink
          class="max-md:hidden flex gap-x-2 items-center md:w-[30%]"
          :to="`/`"
        >
          <img src="~/assets/img/red-logo.svg" alt="" />
          <img
            src="~/assets/img/airbnb-logo-typing.png"
            class="w-[70px]"
            alt=""
          />
        </NuxtLink>
        <div
          class="flex max-md:flex-col max-md:items-start items-center rounded-full py-2 pl-2 pr-2 shadow border font-[500] cursor-pointer hover:shadow-lg transition-all ease max-md:w-full relative"
          @click="openSearchModal()"
        >
          <p class="px-4 md:border-r border-gray-300 max-md:hidden">Aksesoris</p>
          <div class="flex max-md:gap-x-2 max-md:pl-4 max-md:pr-6">
            <p class="md:px-4 md:border-r border-gray-300 max-md:font-light max-md:hidden">
              Perhiasan
            </p>
            <p class="md:px-4 font-light max-md:hidden">Cari barang</p>
            <p class="md:px-4 font-light md:hidden">Cari</p>
          </div>
          <div
            class="w-7 h-7 p-1.5 grid place-items-center rounded-full bg-[#ff5a5f] max-md:absolute right-4 max-md:top-[50%] max-md:-translate-y-[50%]"
          >
            <img src="~/assets/img/search.svg" alt="" />
          </div>
        </div>
        <div class="flex items-center md:w-[30%]">
          <div
            class="py-[3px] max-md:hidden px-4 hover:bg-gray-50 grid place-items-center rounded-full cursor-pointer h-10 font-semibold transition-all ease"
          >
            <span class="text-sm">Penuhi kebutuhan anda</span>
          </div>
          <NuxtLink
            to="/cart"
            class="p-2 ,l-3 hover:bg-gray-50 grid place-items-center rounded-full cursor-pointer transition-all ease"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-6 h-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z"
              />
            </svg>
          </NuxtLink>
          <div
            @click="openUserAction()"
            class="relative p-2 border flex gap-x-2 items-center ml-3.5 rounded-full hover:shadow-lg transition-all ease cursor-pointer group"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-6 h-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
              />
            </svg>
            <div
              class="w-7 h-7 p-[2px] grid place-items-center rounded-full bg-[#717171] overflow-y-hidden"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="#fff"
                viewBox="0 0 24 24"
                stroke-width="1"
                stroke="#fff"
                class="w-6 h-6 translate-y-1"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z"
                />
              </svg>
            </div>
            <div
              class="absolute top-14 right-0 w-[18rem] bg-white rounded-lg shadow border z-[100] cursor-default hidden user-action py-1"
            >
              <NuxtLink v-if="user" to="/" class="w-full py-3 px-5 hover:bg-slate-100 block ">Profil</NuxtLink>
              <NuxtLink v-if="user == ``" to="/login" class="w-full py-3 px-5 hover:bg-slate-100 block ">Login</NuxtLink>
              <button v-else class="w-full py-3 px-5 hover:bg-slate-100 block text-start" @click="handleLogout()">Logout</button>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <slot />
  <!-- SEARCH MODAL -->
  <form
    v-on:submit="e.preventDefault()"
    :action="`/search/${question}`"
    class="fixed left-[50%] -translate-x-[50%] -top-96 md:w-[35rem] w-[95%] py-4 px-5 bg-white rounded-xl z-50 border shadow search-modal transition-all ease duration-500 scale-0"
  >
    <div class="grid grid-cols-12 gap-x-2">
      <input
        type="text"
        class="col-span-10 px-3 py-2 outline-none border-b border-white focus:border-gray-300"
        placeholder="Cari barang"
        v-model="question"
        name="q"
      />
      <button type="button" @click="closeSearchModal()">
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
      <NuxtLink
        :to="`/search/${question}`"
        class="w-7 h-7 p-1.5 grid place-items-center rounded-full bg-[#ff5a5f] self-center"
      >
        <img src="~/assets/img/search.svg" alt="" />
      </NuxtLink>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      question: "",
      user: "",
    };
  },
  methods: {
    handleLogout() {
      localStorage.setItem("user", `0`);
      location.reload()
    },
    openSearchModal() {
      const searchModal = document.querySelector(".search-modal");
      searchModal.classList.toggle("-top-96");
      searchModal.classList.toggle("scale-0");
      searchModal.classList.toggle("top-4");
      searchModal.classList.toggle("scale-100");
    },
    closeSearchModal() {
      const searchModal = document.querySelector(".search-modal");
      searchModal.classList.add("-top-96");
      searchModal.classList.add("scale-0");
      searchModal.classList.remove("top-4");
      searchModal.classList.remove("scale-100");
    },
    openUserAction() {
      const userAction = document.querySelector(".user-action");
      userAction.classList.toggle("hidden");
    },
  },
  mounted() {
    if (process.client) {
      const data = JSON.parse(localStorage.getItem("user")) || "";
      this.user = data;
    }
  },
};
</script>
