<template>
  <div class="main-content">
    <ReservationNavbar />
    <main class="md:py-20 md:pl-24 md:pr-32 max-md:p-5 max-md:pb-32 max-md:overflow-x-hidden">
      <div class="relative">
        <NuxtLink
          :to="`/cart`"
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
        <p class="text-3xl font-semibold relative left-6 max-md:text-2xl">
          Konfirmasikan dan bayar
        </p>
      </div>
      <div class="md:ml-6 grid md:grid-cols-2">
        <div class="pb-8 self-start md:min-h-[150vh]">
          <div class="mt-10 py-4 px-5 border rounded-xl relative">
            <div>
              <p class="font-semibold">Harga lebih rendah</p>
              <p class="mt-2 w-[80%]">
                Goomerce menyediakan banyak diskon untuk setiap produk. Ayo
                dapatkan dan pesan sekarang juga!
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
            <p class="font-semibold text-2xl">Barang</p>
          </div>
          <div
            v-for="data in products"
            class="mt-6 flex justify-between pb-3 border-b"
          >
            <div>
              <p class="font-semibold text-lg">{{ data.title }}</p>
              <p class="">
                Rp.
                {{
                  (
                    data.price * 14987 -
                    data.price * 14987 * (data.discountPercentage / 100)
                  ).toLocaleString()
                }}
              </p>
              <p class="">x {{ data.quantity }} pcs</p>
            </div>
            <div>
              <p class="font-semibold">
                <span class="font-semibold text-lg"
                  >Rp.
                  {{
                    (
                      (data.price * 14987 -
                        data.price * 14987 * (data.discountPercentage / 100)) *
                      data.quantity
                    ).toLocaleString("id-ID")
                  }}</span
                >
              </p>
            </div>
          </div>
          <RegisterCard />
        </div>
        <div class="md:pl-24 md:mt-10 max-md:hidden">
          <div class="py-4 px-5 border rounded-xl md:sticky md:top-20">
            <div class="flex gap-x-3 mb-6">
              <div class="">
                <img
                  src="https://images.unsplash.com/photo-1569180880150-df4eed93c90b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8bWFya2V0fGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60"
                  class="w-32 aspect-square object-cover rounded-lg"
                  alt=""
                />
              </div>
              <div class="flex flex-col justify-between">
                <div>
                  <p class="text-xs text-gray-800">gocomerce</p>
                  <p class="uppercase text-gray-800">banyak diskon</p>
                </div>
                <div>
                  <div class="flex items-center gap-x-1">
                    <p class="text-xs text-slate-500">
                      <span>Buat pesanan sekarang</span>
                    </p>
                  </div>
                </div>
              </div>
            </div>
            <div class="py-5 border-y">
              <p class="font-semibold text-2xl mb-5 text-gray-800">
                Perincian Harga
              </p>
              <div
                v-for="data in products"
                class="flex justify-between text-slate-600 mb-3"
              >
                <p class="">{{ data.title }}</p>
                <p class="">
                  Rp.
                  {{
                    (
                      (data.price * 14987 -
                        data.price * 14987 * (data.discountPercentage / 100)) *
                      data.quantity
                    ).toLocaleString("id-ID")
                  }}
                </p>
              </div>
            </div>
            <div class="pt-5 flex justify-between font-semibold pb-2">
              <p>Total (IDR)</p>
              <p>Rp. {{ total.toLocaleString() }}</p>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
  <!-- TOTAL FIXED -->
  <div class="pt-5 flex justify-between font-semibold py-4 fixed bottom-0 bg-white w-full border-t px-4">
    <p>Total (IDR)</p>
    <p>Rp. {{ total.toLocaleString() }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: null,
      products: [],
      total: 0,
    };
  },
  mounted() {
    if (process.client) {
      this.products = JSON.parse(localStorage.getItem("products"));
      if (this.products?.length > 0) {
        for (let i = 0; i < this.products.length; i++) {
          this.total +=
            (this.products[i].price * 14987 -
              this.products[i].price *
                14987 *
                (this.products[i].discountPercentage / 100)) *
            this.products[i].quantity;
        }
      }
    }
  },
};
</script>
