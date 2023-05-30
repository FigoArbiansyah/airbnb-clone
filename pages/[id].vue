<template>
  <div class="main-content">
    <DetailNavbar />
    <main class="min-h-screen">
      <section class="relative mt-5 md:px-[115px] px-3">
        <div class="mt-3">
          <p class="text-2xl font-semibold">{{ data?.title }}</p>
        </div>
        <div class="flex justify-between items-center mt-2 w-full">
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
              <span class="underline">365 ulasan</span>
              .
              <span class="underline capitalize">{{ data.category }}</span>
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
        <div class="mt-6 flex rounded-xl overflow-hidden">
          <div class="w-1/2 md:pr-1">
            <img
              :src="data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
          </div>
          <div class="w-1/2 md:pl-1 grid gap-2 grid-cols-2">
            <img
              :src="data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
            <img
              :src="data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
            <img
              :src="data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
            <img
              :src="data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover"
            />
          </div>
        </div>
      </section>
      <section
        class="mt-8 grid md:grid-cols-3 grid-cols-1 gap-x-16 md:px-[115px] px-3 relative"
      >
        <div class="md:col-span-2 min-h-[200vh]">
          <div
            class="flex gap-2 w-full justify-between items-center border-b pb-5"
          >
            <div>
              <p class="text-2xl font-semibold text-gray-700">
                Seluruh vila. Tuan rumah: Ari & Kim ,
              </p>
              <p class="text-gray-500">
                <span>8 tamu</span>
                .
                <span>2 kamar tidur</span>
                .
                <span>4 tempat tidur</span>
                .
                <span>3 tempat mandi</span>
              </p>
            </div>
            <div>
              <img
                src="~/assets/img/profile.webp"
                class="w-14 h-14 rounded-full"
                alt=""
              />
            </div>
          </div>
          <div class="mt-5">
            <p class="text-gray-800">
              {{ data?.description }}. Vila mewah baru di Bali Utara dengan
              pemandangan laut yang menakjubkan dan tidak terganggu. Selesai
              pada tahun 2015, Kami memiliki 3 tempat yang hampir sama, jadi
              silakan lihat 2 tempat lainnya untuk berjaga - jaga jika tempat
              ini terpesan.
            </p>
          </div>
        </div>
        <div class="border p-5 rounded-xl sticky top-8 self-start shadow">
          <p v-if="data.discountPercentage">
            <span class="text-xl font-semibold text-gray-700 line-through"
              >Rp {{ (data.price * 14987).toLocaleString("id-ID") }}
            </span>
            <span class="text-xl font-semibold">
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
              <span class="underline text-gray-700">365 ulasan</span>
            </p>
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
    return { data: [] };
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
