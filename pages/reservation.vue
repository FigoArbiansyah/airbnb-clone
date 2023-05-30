<template>
  <div class="main-content">
    <ReservationNavbar />
    <main class="md:py-20 md:pl-24 md:pr-32 max-md:p-5">
      <div class="relative">
        <NuxtLink
          :to="`/${id}`"
          class="cursor-pointer w-10 h-10 rounded-full grid place-items-center hover:bg-gray-100 absolute top-0 -left-4"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="#000"
            class="w-4 h-4"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M15.75 19.5L8.25 12l7.5-7.5"
            />
          </svg>
        </NuxtLink>
        <p class="text-3xl font-semibold relative left-6">
          Konfirmasikan dan bayar
        </p>
      </div>
      <div class="md:ml-6 grid grid-cols-2">
        <div class="pb-8 border-b">
          <div class="mt-10 py-4 px-5 border rounded-xl relative">
            <div>
              <p class="font-semibold">Harga lebih rendah</p>
              <p class="mt-2 w-[80%]">
                Harga untuk tanggal pilihan Anda lebih murah Rp3951062 dari
                harga per malam rata-rata 60 hari terakhir.
              </p>
            </div>
            <svg
              class="absolute top-5 right-10"
              viewBox="0 0 48 48"
              xmlns="http://www.w3.org/2000/svg"
              aria-hidden="true"
              role="presentation"
              focusable="false"
              style="
                display: block;
                height: 32px;
                width: 32px;
                fill: rgb(227, 28, 95);
                stroke: currentcolor;
              "
            >
              <g stroke="none">
                <path
                  d="M24.556 8H9a1 1 0 0 0-.993.883L8 9v15.556a1 1 0 0 0 .206.608l.087.1 17.213 17.213a1 1 0 0 0 1.32.083l.094-.083L42.477 26.92a1 1 0 0 0 .083-1.32l-.083-.094L25.263 8.293a1 1 0 0 0-.575-.284L24.556 8z"
                  fill-opacity=".2"
                ></path>
                <path
                  d="M24.556 4A5 5 0 0 1 27.9 5.282l.192.182 17.213 17.214a5 5 0 0 1 .172 6.89l-.172.18L29.75 45.306a5 5 0 0 1-6.89.172l-.181-.172L5.464 28.092a5 5 0 0 1-1.457-3.271L4 24.556V9a5 5 0 0 1 4.783-4.995L9 4h15.556zm0 2H9a3 3 0 0 0-2.995 2.824L6 9v15.556a3 3 0 0 0 .743 1.977l.136.145L24.092 43.89a3 3 0 0 0 4.099.135l.144-.135L43.89 28.335a3 3 0 0 0 .135-4.1l-.135-.143L26.678 6.879a3 3 0 0 0-1.924-.872L24.556 6zM13 10a3 3 0 1 1 0 6 3 3 0 0 1 0-6zm0 2a1 1 0 1 0 0 2 1 1 0 0 0 0-2z"
                ></path>
              </g>
            </svg>
          </div>
          <div class="mt-6">
            <p class="font-semibold text-2xl">Perjalanan Anda</p>
          </div>
          <div class="mt-6 flex justify-between">
            <div>
              <p class="font-semibold text-lg">Tanggal</p>
              <p class="">11-14 Jun</p>
            </div>
            <div>
              <p class="cursor-pointer underline font-semibold">Edit</p>
            </div>
          </div>
          <div class="mt-6 flex justify-between">
            <div>
              <p class="font-semibold text-lg">Tamu</p>
              <p class="">2 tamu</p>
            </div>
            <div>
              <p class="cursor-pointer underline font-semibold">Edit</p>
            </div>
          </div>
        </div>
        <div class="pl-24 mt-10">
          <div class="py-4 px-5 border rounded-xl">
            <div class="flex gap-x-3">
              <div class="">
                <img
                  src="~/assets/img/reservation.webp"
                  class="w-32 aspect-square object-cover rounded-lg"
                  alt=""
                />
              </div>
              <div class="flex flex-col justify-between">
                <div>
                  <p class="text-xs text-gray-800">Seluruh vila</p>
                  <p class="uppercase text-gray-800">
                    180° VIEW, PRIVATE POOL VILLA..
                  </p>
                </div>
                <div>
                  <div class="flex items-center gap-x-1">
                    <svg
                      width="14"
                      height="14"
                      viewBox="0 0 8 8"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M4 0L4.89806 2.76393H7.80423L5.45308 4.47214L6.35114 7.23607L4 5.52786L1.64886 7.23607L2.54692 4.47214L0.195774 2.76393H3.10194L4 0Z"
                        fill="#000"
                      />
                    </svg>
                    <p class="text-xs text-slate-500">
                      <span>4.9 . (365)</span>
                      .
                    </p>
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 16 16"
                      aria-hidden="true"
                      role="presentation"
                      focusable="false"
                      style="
                        display: block;
                        height: 12px;
                        width: 12px;
                        fill: currentcolor;
                      "
                    >
                      <path
                        d="M8.498 7.593l3.1-1.74c.5-.278.99-.552 1.474-.82a.833.833 0 0 0 .428-.729v-2.97A.833.833 0 0 0 12.667.5H3.333a.833.833 0 0 0-.833.833v2.97c0 .303.164.582.428.729l3 1.675 1.575.886c.348.195.647.195.995-.001zM8 8.5a3.5 3.5 0 1 0 0 7 3.5 3.5 0 0 0 0-7z"
                      ></path>
                    </svg>
                    <span class="text-xs text-slate-500">Hos Teladan</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: null,
    };
  },
  mounted() {
    this.id = this.$route.query.id;
  },
};
</script>
