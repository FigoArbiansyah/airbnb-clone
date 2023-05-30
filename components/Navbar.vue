<template>
  <header class="z-50 bg-white md:sticky md:top-0">
    <nav class="py-4 px-[35px] border-y border-gray-200">
      <div class="flex justify-between">
        <div class="max-md:hidden flex gap-x-2 items-center md:w-[30%]">
          <img src="~/assets/img/red-logo.svg" alt="" />
          <img
            src="~/assets/img/airbnb-logo-typing.png"
            class="w-[70px]"
            alt=""
          />
        </div>
        <div
          class="flex max-md:flex-col max-md:items-start items-center rounded-full py-2 pl-2 pr-2 shadow border font-[500] cursor-pointer hover:shadow-lg transition-all ease max-md:w-full"
        >
          <p class="px-4 md:border-r border-gray-300">Ke mana saja</p>
          <div class="flex max-md:gap-x-2 max-md:pl-4 max-md:pr-6">
            <p class="md:px-4 md:border-r border-gray-300 max-md:font-light">
              Minggu mana pun
            </p>
            <p class="md:px-4 font-light">Tambahkan tamu</p>
          </div>
          <div
            class="w-7 h-7 p-1.5 grid place-items-center rounded-full bg-[#ff5a5f] max-md:hidden"
          >
            <img src="~/assets/img/search.svg" alt="" />
          </div>
        </div>
        <div class="max-md:hidden flex gap-x-0 items-center md:w-[30%]">
          <div
            class="py-[3px] px-4 hover:bg-gray-50 grid place-items-center rounded-full cursor-pointer h-10 font-semibold transition-all ease"
          >
            <span class="text-sm">Jadikan rumah Anda Airbnb</span>
          </div>
          <div
            class="p-2 ,l-3 hover:bg-gray-50 grid place-items-center rounded-full cursor-pointer transition-all ease"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#000"
              class="w-6 h-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0112 16.5c-3.162 0-6.133-.815-8.716-2.247m0 0A9.015 9.015 0 013 12c0-1.605.42-3.113 1.157-4.418"
              />
            </svg>
          </div>
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
    <Category />
  </header>
</template>
