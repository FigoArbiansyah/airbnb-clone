<template>
  <header class="z-50 bg-white border-b border-gray-200">
    <nav class="py-4 md:px-[115px] px-3">
      <div class="flex justify-between">
        <a href="/" class="max-md:hidden flex gap-x-2 items-center md:w-[30%]">
          <img src="~/assets/img/red-logo.svg" alt="" />
          <img
            src="~/assets/img/airbnb-logo-typing.png"
            class="w-[70px]"
            alt=""
          />
        </a>
        <div
          class="flex max-md:items-start max-md:justify-between items-center rounded-full py-2 pl-2 pr-2 shadow border font-[500] cursor-pointer hover:shadow-lg transition-all ease max-md:w-full"
        >
          <p class="pl-4 pr-16">Mulai pencarian Anda</p>
          <div
            class="w-7 h-7 p-1.5 grid place-items-center rounded-full bg-[#ff5a5f]"
          >
            <img src="~/assets/img/search.svg" alt="" />
          </div>
        </div>
        <div class="max-md:hidden flex gap-x-0 items-center md:w-[30%]">
          <div
            class="py-[3px] px-1 hover:bg-gray-50 grid place-items-center rounded-full cursor-pointer h-10 font-semibold transition-all ease"
          >
            <span class="text-sm">Penuhi kebutuhan anda</span>
          </div>
          <NuxtLink
            to="/cart"
            class="p-2 ml-3 hover:bg-gray-50 grid place-items-center rounded-full cursor-pointer transition-all ease"
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
            class="p-2 border flex gap-x-2 items-center ml-3.5 rounded-full hover:shadow-lg transition-all ease cursor-pointer"
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
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>
