<template>
  <div class="main-content pb-20">
    <header class="z-50 bg-white">
      <Navbar />
    </header>
    <main class="min-h-screen">
      <section class="relative md:mt-5 md:px-[115px]">
        <div class="mt-3 max-md:hidden">
          <p class="text-2xl font-semibold">{{ data?.title }}</p>
        </div>
        <div class="flex justify-between items-center mt-2 w-full max-md:hidden">
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
            <p class="text-sm">
              <span>{{ data.rating }} . </span>
              <NuxtLink
                :to="`/category/${data.category}`"
                class="underline capitalize"
                >{{ data.category }}</NuxtLink
              >
              .
              <span class="underline">{{ data.brand }}</span>
              .
            </p>
          </div>
          <div class="flex gap-x-3">
            <div class="flex items-center gap-x-1.5">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 20 20"
                fill="#333"
                class="w-4 h-4"
              >
                <path
                  d="M9.25 13.25a.75.75 0 001.5 0V4.636l2.955 3.129a.75.75 0 001.09-1.03l-4.25-4.5a.75.75 0 00-1.09 0l-4.25 4.5a.75.75 0 101.09 1.03L9.25 4.636v8.614z"
                />
                <path
                  d="M3.5 12.75a.75.75 0 00-1.5 0v2.5A2.75 2.75 0 004.75 18h10.5A2.75 2.75 0 0018 15.25v-2.5a.75.75 0 00-1.5 0v2.5c0 .69-.56 1.25-1.25 1.25H4.75c-.69 0-1.25-.56-1.25-1.25v-2.5z"
                />
              </svg>
              <p class="text-sm underline">Bagikan</p>
            </div>
            <div class="flex items-center gap-x-1.5">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="#333"
                class="w-4 h-4"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12z"
                />
              </svg>
              <p class="text-sm underline">Simpan</p>
            </div>
          </div>
        </div>
        <div class="md:mt-6 md:flex md:rounded-xl overflow-hidden max-md:overflow-x-auto image-swipe">
          <div class="md:w-1/2 md:pr-1 max-md:hidden">
            <img
              :src="data?.thumbnail"
              alt=""
              class="w-full md:aspect-video aspect-square max-md:h-full object-cover"
            />
          </div>
          <div v-if="data.images" class="md:w-1/2 md:pl-1 md:grid md:gap-2 grid-cols-2 max-md:flex" >
            <img
              :src="data?.thumbnail"
              alt=""
              class="md:hidden w-full md:aspect-video aspect-square max-md:h-full object-cover"
            />
            <img
              :src="data?.images[0] || data?.thumbnail"
              alt=""
              class="w-full md:aspect-video aspect-square max-md:h-full object-cover"
            />
            <img
              :src="data?.images[1] || data?.thumbnail"
              alt=""
              class="w-full md:aspect-video aspect-square max-md:h-full object-cover"
            />
            <img
              :src="data?.images[2] || data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
            <img
              :src="data?.images[3] || data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
          </div>
        </div>
      </section>
      <section
        class="mt-8 grid md:grid-cols-12 grid-cols-1 gap-16 md:px-[115px] px-5 relative"
      >
        <div class="md:col-span-7">
          <div
            class="flex gap-2 w-full justify-between items-center border-b pb-5"
          >
            <div>
              <p class="text-2xl font-semibold text-gray-700">
                {{ data.title }}
              </p>
              <p class="text-gray-500">
                <NuxtLink
                  :to="`/category/${data.category}`"
                  class="underline"
                  >{{ data.category }}</NuxtLink
                >
                .
                <span>{{ data.brand }}</span>
              </p>
            </div>
            <!-- <div>
              <img
                src="~/assets/img/profile.webp"
                class="w-14 h-14 rounded-full"
                alt=""
              />
            </div> -->
          </div>
          <div class="mt-5 pb-5 border-b">
            <div class="flex items-center gap-x-3">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-10 h-10"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M9 14.25l6-6m4.5-3.493V21.75l-3.75-1.5-3.75 1.5-3.75-1.5-3.75 1.5V4.757c0-1.108.806-2.057 1.907-2.185a48.507 48.507 0 0111.186 0c1.1.128 1.907 1.077 1.907 2.185zM9.75 9h.008v.008H9.75V9zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm4.125 4.5h.008v.008h-.008V13.5zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z"
                />
              </svg>
              <div class="md:w-10/12 w-[80%]">
                <p class="text-lg font-semibold">
                  {{ data.discountPercentage }}%
                </p>
                <p class="text-gray-500 text-sm mt-1.5">Diskon.</p>
              </div>
            </div>
          </div>
          <div class="mt-5">
            <p class="text-gray-800">{{ data?.description }}.</p>
          </div>
        </div>
        <div
          class="md:col-span-5 border p-5 rounded-xl sticky top-8 self-start shadow"
        >
          <div>
            <p v-if="data.discountPercentage">
              <span class="text-xl font-semibold text-gray-700 line-through"
                >Rp {{ (data.price * 14987).toLocaleString("id-ID") }}
              </span>
              <span class="text-xl font-semibold float-right">
                Rp
                {{
                  (
                    data.price * 14987 -
                    data.price * 14987 * (data.discountPercentage / 100)
                  ).toLocaleString("id-ID")
                }}</span
              >
            </p>
            <p v-else>
              <span class="text-xl font-semibold text-gray-700"
                >Rp {{ (data.price * 14987).toLocaleString("id-ID") }}</span
              >
            </p>
          </div>
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
            <p class="text-sm">
              <span>{{ data.rating }} . </span>
            </p>
          </div>
          <p class="text-gray-700">stok: {{ data.stock }}</p>
          <div class="mt-3 grid grid-cols-2 rounded-lg overflow-hidden">
            <div
              class="col-span-2 border py-2.5 px-3 flex justify-between items-center"
            >
              <p class="uppercase font-semibold">Jumlah</p>
              <div class="flex gap-x-5 text-xl items-center">
                <button class="p-3" @click="qty -= 1" :disabled="qty == 1">
                  -
                </button>
                <p>{{ qty }}</p>
                <button
                  class="p-3"
                  @click="qty += 1"
                  :disabled="qty == data.stock"
                >
                  +
                </button>
              </div>
            </div>
          </div>
          <div class="mt-4 text-center">
            <button class="w-full" @click="setCart()">
              <div
                class="w-full text-center py-3 bg-[#EF5A5F] hover:bg-[#FF5F5C] rounded-xl font-semibold text-white transition-all ease"
              >
                Pesan
              </div>
            </button>
            <p class="text-gray-600 mt-3">Anda belum dikenakan biaya</p>
            <div class="mt-5 flex justify-between pb-5 border-b">
              <p class="underline">
                Rp
                {{
                  (
                    data.price * 14987 -
                    data.price * 14987 * (data.discountPercentage / 100)
                  ).toLocaleString("id-ID")
                }}
                x {{ qty }}
              </p>
              <p class="">
                Rp
                {{
                  (
                    (data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)) *
                    qty
                  ).toLocaleString("id-ID")
                }}
              </p>
            </div>
            <div class="pt-5 flex justify-between text-black">
              <p class="font-semibold">Total</p>
              <p class="font-semibold">
                Rp
                {{
                  (
                    (data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)) *
                    qty
                  ).toLocaleString("id-ID")
                }}
              </p>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      data: [],
      qty: 1,
      body: {
        userId: 1,
        products: [{ id: this.$route.params.id, quantity: this.qty }],
      },
    };
  },
  async created() {
    this.getData();
  },
  methods: {
    async getData() {
      const route = useRoute();
      const id = route.params.id;
      try {
        const res = await axios.get("https://dummyjson.com/products/" + id);
        this.data = await res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async setCart() {
      try {
        const user = JSON.parse(localStorage.getItem("user")) || "";
        if (user == 0 || user == "") {
          alert("Login terlebih dahulu");
          return false;
        } else {
          const carts = JSON.parse(localStorage.getItem("carts")) || [];
          const newData = {
            userId: user?.id,
            id: this.$route.params.id,
            title: this.data.title,
            price: this.data.price,
            quantity: this.qty,
            total: this.data.price * this.qty,
            discountPercentage: this.data.discountPercentage,
            discountedPrice:
              this.data.price -
              this.data.price * (this.data.discountPercentage / 100),
          };
          // CEK KESAMAAN DATA BARANG
          const isAvailable = carts.some(cart => cart.id == newData.id && cart.userId == newData.userId)
          if (isAvailable) {
            for (let i = 0; i < carts.length; i++) {
              if (newData.userId == carts[i].userId && newData.id == carts[i].id) {
                carts[i].quantity += newData.quantity
                localStorage.setItem("carts", JSON.stringify(carts));
                alert('Barang sudah ada, kuantitas telah ditambahkan')
              }
            }
          } else {
            carts.push(newData);
            localStorage.setItem("carts", JSON.stringify(carts));
            alert("Berhasil menambahkan barang ke keranjang");
          }
        }
      } catch (error) {
        console.log(error);
      }
    },
    scrollToNext(id) {
      const images = document.querySelector(".images" + id);
      images.scrollLeft += images.offsetWidth;
    },
    scrollToPrev(id) {
      const images = document.querySelector(".images" + id);
      images.scrollLeft -= images.offsetWidth;
    },
  },
};
</script>

<style scope>
.image-swipe::-webkit-scrollbar-track
{
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.1);
    background-color: #F5F5F5; 
}

.image-swipe::-webkit-scrollbar
{
  height: 12px;
    width: 10px;
    background-color: #F5F5F5;
}

.image-swipe::-webkit-scrollbar-thumb
{
  height: 4px;
    border-radius: 10px;
    background-color: #FFF;
    background-image: -webkit-linear-gradient(right,
  #FF5F5C 0%,
  #EF5A5F 50%,
  #EF5A5F 51%,
  #FF5F5C 100%);
}
</style>