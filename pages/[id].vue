<template>
  <div class="main-content pb-20">
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
        class="mt-8 grid md:grid-cols-12 grid-cols-1 gap-16 md:px-[115px] px-3 relative"
      >
        <div class="md:col-span-7 md:min-h-[200vh]">
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
            <!-- <div>
              <img
                src="~/assets/img/profile.webp"
                class="w-14 h-14 rounded-full"
                alt=""
              />
            </div> -->
          </div>
          <div class="mt-5 pb-5 border-b">
            <div class="flex items-start gap-x-3">
              <svg
                viewBox="0 0 32 32"
                xmlns="http://www.w3.org/2000/svg"
                aria-hidden="true"
                role="presentation"
                focusable="false"
                class="md:w-1/12 w-[10%] mt-2"
                style="
                  display: block;
                  height: 24px;
                  width: 24px;
                  fill: currentcolor;
                "
              >
                <path
                  d="M26 2a1 1 0 0 1 .922.612l.04.113 2 7a1 1 0 0 1-.847 1.269L28 11h-3v5h6v2h-2v13h-2l.001-2.536a3.976 3.976 0 0 1-1.73.527L25 29H7a3.982 3.982 0 0 1-2-.535V31H3V18H1v-2h5v-4a1 1 0 0 1 .883-.993L7 11h.238L6.086 8.406l1.828-.812L9.427 11H12a1 1 0 0 1 .993.883L13 12v4h10v-5h-3a1 1 0 0 1-.987-1.162l.025-.113 2-7a1 1 0 0 1 .842-.718L22 2h4zm1 16H5v7a2 2 0 0 0 1.697 1.977l.154.018L7 27h18a2 2 0 0 0 1.995-1.85L27 25v-7zm-16-5H8v3h3v-3zm14.245-9h-2.491l-1.429 5h5.349l-1.429-5z"
                ></path>
              </svg>
              <div class="md:w-10/12 w-[80%]">
                <p class="font-semibold">Area kerja khusus.</p>
                <p class="text-gray-500 text-sm mt-1.5">
                  Kamar dengan wifi yang cocok untuk bekerja.
                </p>
              </div>
            </div>
            <div class="flex items-start mt-4 gap-x-3">
              <svg
                viewBox="0 0 32 32"
                xmlns="http://www.w3.org/2000/svg"
                aria-hidden="true"
                role="presentation"
                focusable="false"
                class="md:w-1/12 w-[10%] mt-2"
                style="
                  display: block;
                  height: 24px;
                  width: 24px;
                  fill: currentcolor;
                "
              >
                <path
                  d="m24.3334 1.66675c1.0543745 0 1.9181663.81587127 1.9945143 1.85073677l.0054857.14926323-.00065 24.666 3.00065.00075v2h-26.66665v-2l3-.00075v-24.666c0-1.05436681.81587301-1.91816558 1.850737-1.99451429l.149263-.00548571zm-4.00065 2h-12.666l-.00075 24.66625 12.66675-.00025zm4.00065 0h-2.00065v24.666l2.00025.00025zm-7.0001 11.00002c.7363778 0 1.33333.5969522 1.33333 1.33333s-.5969522 1.33333-1.33333 1.33333-1.33333-.5969522-1.33333-1.33333.5969522-1.33333 1.33333-1.33333z"
                ></path>
              </svg>
              <div class="md:w-10/12 w-[80%]">
                <p class="font-semibold">Check-in mandiri.</p>
                <p class="text-gray-500 text-sm mt-1.5">
                  Anda bisa check-in dengan dibantu penjaga pintu.
                </p>
              </div>
            </div>
            <div class="flex items-start mt-4 gap-x-3">
              <svg
                viewBox="0 0 32 32"
                xmlns="http://www.w3.org/2000/svg"
                aria-hidden="true"
                role="presentation"
                focusable="false"
                class="md:w-1/12 w-[10%] mt-2"
                style="
                  display: block;
                  height: 24px;
                  width: 24px;
                  fill: currentcolor;
                "
              >
                <path
                  d="m16 17c3.8659932 0 7 3.1340068 7 7s-3.1340068 7-7 7-7-3.1340068-7-7 3.1340068-7 7-7zm0 2c-2.7614237 0-5 2.2385763-5 5s2.2385763 5 5 5 5-2.2385763 5-5-2.2385763-5-5-5zm9.6666667-18.66666667c1.0543618 0 1.9181651.81587779 1.9945142 1.85073766l.0054858.14926234v6.38196601c0 .70343383-.3690449 1.35080636-.9642646 1.71094856l-.1413082.0779058-9.6666667 4.8333334c-.5067495.2533747-1.0942474.2787122-1.6171466.0760124l-.1717078-.0760124-9.66666666-4.8333334c-.62917034-.3145851-1.04315599-.93418273-1.09908674-1.62762387l-.00648607-.16123049v-6.38196601c0-1.05436179.81587779-1.91816512 1.85073766-1.99451426l.14926234-.00548574zm0 2h-19.33333337v6.38196601l9.66666667 4.83333336 9.6666667-4.83333336z"
                ></path>
              </svg>
              <div class="md:w-10/12 w-[80%]">
                <p class="font-semibold">
                  Ari & Kim , adalah seorang HosTeladan.
                </p>
                <p class="text-gray-500 text-sm mt-1.5">
                  HosTeladan adalah tuan rumah berpengalaman dan berpenilaian
                  tinggi yang berkomitmen dalam menyediakan penginapan luar
                  biasa bagi tamu.
                </p>
              </div>
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
              <span class="underline text-gray-700">365 ulasan</span>
            </p>
          </div>
          <div class="mt-3 grid grid-cols-2 rounded-lg overflow-hidden">
            <div class="border py-2.5 px-3">
              <p class="text-xs uppercase font-semibold">check-in</p>
              <p class="">11/6/2023</p>
            </div>
            <div class="border py-2.5 px-3">
              <p class="text-xs uppercase font-semibold">check-out</p>
              <p class="">14/6/2023</p>
            </div>
            <div class="col-span-2 border py-2.5 px-3">
              <p class="text-xs uppercase font-semibold">tamu</p>
              <p class="">2 tamu</p>
            </div>
          </div>
          <div class="mt-4 text-center">
            <NuxtLink :to="`/reservation?id=${data.id}`"
              ><div
                class="w-full text-center py-3 bg-[#EF5A5F] hover:bg-[#FF5F5C] rounded-xl font-semibold text-white transition-all ease"
              >
                Pesan
              </div></NuxtLink
            >
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
                x 3 malam
              </p>
              <p class="">
                Rp
                {{
                  (
                    (data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)) *
                    3
                  ).toLocaleString("id-ID")
                }}
              </p>
            </div>
            <div class="pt-5 flex justify-between text-black">
              <p class="font-semibold">Total sebelum pajak</p>
              <p class="font-semibold">
                Rp
                {{
                  (
                    (data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)) *
                    3
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
