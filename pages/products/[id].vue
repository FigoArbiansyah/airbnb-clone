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
        <div class="md:mt-6 md:flex md:rounded-xl overflow-hidden max-md:hidden max-md:overflow-x-auto image-swipe">
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
              v-if="data?.images?.lentgh != 0"
              v-for="image in data?.images"
              :src="image"
              alt=""
              class="w-full md:aspect-video aspect-square max-md:h-full object-cover md:hidden"
            />
            <img
              :src="data?.images[0] || data?.thumbnail"
              alt=""
              class="w-full md:aspect-video aspect-square max-md:h-full object-cover max-md:hidden"
            />
            <img
              :src="data?.images[1] || data?.thumbnail"
              alt=""
              class="w-full md:aspect-video aspect-square max-md:h-full object-cover max-md:hidden"
            />
            <img
              :src="data?.images[2] || data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover max-md:hidden"
            />
            <img
              :src="data?.images[3] || data?.thumbnail"
              alt=""
              class="w-full aspect-video object-cover max-md:hidden"
            />
          </div>
        </div>
        <div class="md:hidden">
          <swiper
            direction="horizontal"
            :slides-per-view="1"
            navigation
            :pagination="{ clickable: false }"
            @swiper="onSwiper"
            @slideChange="onSlideChange"
            :modules="modules" 
            class="md:hidden flex max-md:overflow-x-auto">
            <swiper-slide class="md:w-1/2 md:pr-1 md:hidden">
              <img
                :src="data?.thumbnail"
                alt=""
                class="w-full md:aspect-video aspect-square max-md:h-full object-cover"
              />
            </swiper-slide>
            <swiper-slide v-if="data?.images?.lentgh != 0" v-for="image in data?.images" class="md:w-1/2 md:pl-1 md:grid md:gap-2 grid-cols-2 max-md:flex md:hidden" >
              <img
                :src="image"
                alt=""
                class="w-full md:aspect-video aspect-square max-md:h-full object-cover "
              />
            </swiper-slide>
          </swiper>
        </div>
      </section>
      <section
        class="mt-8 grid md:grid-cols-12 grid-cols-1 gap-16 md:px-[115px] px-5 relative"
      >
        <div class="md:col-span-7">
          <div
            class="w-full border-b pb-5"
          >
            <div>
              <p class="text-2xl font-semibold text-gray-700">
                {{ data.title }}
              </p>
              <div class="mt-4 py-1 px-3 bg-[#FF5F5C] text-white w-auto inline-block rounded">{{data.discountPercentage}}%</div>
              
            </div>
          </div>
          <div class="mt-5 max-md:pb-12">
            <table>
              <tr>
                <td>Kategori</td>
                <td>&nbsp; : &nbsp;</td>
                <td>
                  <NuxtLink
                  :to="`/category/${data.category}`"
                  class="underline"
                  >{{ data.category }}</NuxtLink>
                </td>
              </tr>
              <tr>
                <td>Brand</td>
                <td>&nbsp; : &nbsp;</td>
                <td>{{data.brand}}</td>
              </tr>
              <tr>
                <td>Tersisa</td>
                <td>&nbsp; : &nbsp;</td>
                <td>{{data.stock}} pcs</td>
              </tr>
              <tr>
                <td>Rate</td>
                <td>&nbsp; : &nbsp;</td>
                <td>{{data.rating}} / 5</td>
              </tr>
            </table>
            <p class="text-gray-800 mt-2">{{ data?.description }}.</p>
            <p class="text-gray-800 mt-2">Produk ini merupakan hasil inovasi terbaru yang dirancang untuk memenuhi kebutuhan dan keinginan konsumen modern. Dengan menggabungkan teknologi canggih, desain estetika yang menawan, dan kinerja yang luar biasa, produk ini hadir sebagai solusi yang sempurna untuk memudahkan kehidupan sehari-hari.
            </p>
            <div v-if="deskripsiShow" @click="deskripsiShow = !deskripsiShow" class="mb-2 cursor-pointer">
              <p class="text-gray-800 mt-2">Produk ini merupakan hasil inovasi terbaru yang dirancang untuk memenuhi kebutuhan dan keinginan konsumen modern. Dengan menggabungkan teknologi canggih, desain estetika yang menawan, dan kinerja yang luar biasa, produk ini hadir sebagai solusi yang sempurna untuk memudahkan kehidupan sehari-hari.
              </p>
              <p class="text-gray-800 mt-2">Produk ini menghadirkan fitur yang sangat berguna dan dapat digunakan dalam berbagai situasi. Dengan menggunakan produk ini, Anda dapat meningkatkan produktivitas, efisiensi, dan kenyamanan. Desain yang ergonomis dan intuitif membuat penggunaan produk ini menjadi mudah dan menyenangkan.
              </p>
              <p class="text-gray-800 mt-2">Kualitas produk ini sangatlah tinggi, dengan bahan-bahan terbaik dan konstruksi yang kokoh, sehingga memberikan daya tahan yang luar biasa. Produk ini juga dirancang untuk memberikan performa yang optimal dan dapat diandalkan dalam jangka panjang.
              </p>
              <p class="text-gray-800 mt-2">Dalam produk ini, fokus utama adalah pada keamanan dan keandalan. Setiap detail dan fitur produk ini telah dirancang dengan teliti untuk memastikan penggunaan yang aman dan terjamin.
              </p>
              <p class="text-gray-800 mt-2">Produk ini hadir dengan beragam pilihan dan variasi, sehingga Anda dapat memilih yang sesuai dengan kebutuhan dan gaya hidup Anda. Dengan berbagai opsi yang tersedia, produk ini dapat memenuhi kebutuhan semua kalangan, mulai dari profesional hingga pengguna pribadi.
              </p>
              <p class="text-gray-800 mt-2">Dengan keunggulan dan keistimewaannya, produk ini menjadi pilihan yang sempurna bagi mereka yang menginginkan pengalaman terbaik dalam penggunaan produk yang dapat memenuhi harapan dan memberikan nilai lebih.
              </p>
            </div>
            <p class="underline mt-2 cursor-pointer mb-3" @click="deskripsiShow = !deskripsiShow"><span v-if="!deskripsiShow">Lihat selengkapnya</span><span v-else>Lihat lebih sedikit</span></p>
            <div class="mb-3 md:hidden">
              <button @click="openCartForm()" class="py-2 px-4 bg-[#ff5f5c] rounded border border-white text-white hover:border-[#ff5f5c] hover:bg-transparent hover:text-[#ff5f5c] transition-all ease duration-300">
                <span class="pesan">Pesan sekarang</span>
                <span class="batal hidden">Batalkan</span>
              </button>
            </div>
            <div class="text-2xl font-semibold text-gray-700 py-4 border-t">
              Ulasan
            </div>
            <div class="grid md:grid-cols-2 gap-5">
              <div v-for="data in ulasan">
                <div class="flex gap-x-3 items-center">
                  <div>
                    <img :src="data.img" class="w-20 aspect-square rounded-full object-cover border" alt="">
                  </div>
                  <div>
                    <p class="font-semibold">{{ data.name }}</p>
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
                        <span>{{ data.rate }}</span>
                      </p>
                    </div>
                  </div>
                </div>
                <div class="mt-4">
                  <p class="text-gray-700">{{ data.message }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div
          class="md:block cart-form md:col-span-5 md:border p-5 md:rounded-xl md:sticky md:top-8 self-start md:shadow max-md:fixed max-md:-bottom-64 max-md:left-0 max-md:w-full max-md:bg-white z-50 transition-all ease duration-500"
        >
          <div class="md:hidden flex justify-between max-md:flex-col max-md:items-start gap-y-2 text-black float-right">
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
          <div>
            <p v-if="data.discountPercentage">
              <span class="md:text-xl text-lg font-semibold text-gray-500 line-through"
                >Rp {{ (data.price * 14987).toLocaleString("id-ID") }}
              </span>
              <br class="md:hidden" />
              <span class="md:text-xl text-lg font-semibold md:float-right">
                Rp
                {{
                  (
                    data.price * 14987 -
                    data.price * 14987 * (data.discountPercentage / 100)
                  ).toLocaleString("id-ID").split(",")[0]
                }}</span
              >
            </p>
            <p v-else>
              <span class="md:text-xl text-lg font-semibold text-gray-700"
                >Rp {{ (data.price * 14987).toLocaleString("id-ID") }}</span
              >
            </p>
          </div>
          <div class="flex items-center gap-x-1 mt-2 max-md:hidden">
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
            <p class="text-gray-600 mt-3 max-md:hidden">Anda belum dikenakan biaya</p>
            <div class="mt-5 flex justify-between max-md:flex-col max-md:items-start gap-y-2 pb-5 border-b max-md:hidden">
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
            <div class="pt-5 flex justify-between max-md:flex-col max-md:items-start max-md:hidden gap-y-2 text-black">
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
  <Footer />
</template>

<script>
import axios from "axios";
import { Navigation, Pagination } from 'swiper';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      data: [],
      qty: 1,
      body: {
        userId: 1,
        products: [{ id: this.$route.params.id, quantity: this.qty }],
      },
      deskripsiShow: false,
      ulasan: [
        {
          id: 1,
          img: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NHx8dXNlciUyMHByb2ZpbGV8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=500&q=60",
          name: "Deddy Corbuzier",
          rate: 4.5,
          message: "Saya selalu menggunakan barang ini pada saat podcast dan berkumpul bersama keluarga. Direkomendasikan!",
          date: "13-04-2023",
        },
        {
          id: 2,
          img: "https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NXx8dXNlciUyMHByb2ZpbGV8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=500&q=60",
          name: "Agnes Monica",
          rate: 4.5,
          message: "Bahkan saat saya sedang di panggung, saya selalu teringat dengan barang ini!",
          date: "13-04-2023",
        },
        {
          id: 3,
          img: "https://images.unsplash.com/photo-1531727991582-cfd25ce79613?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mzd8fHVzZXIlMjBwcm9maWxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
          name: "Rossa",
          rate: 4.5,
          message: "Ini barang yang cantik dan saya menyukainya!",
          date: "13-04-2023",
        },
        {
          id: 4,
          img: "https://images.unsplash.com/photo-1619895862022-09114b41f16f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mzl8fHVzZXIlMjBwcm9maWxlfGVufDB8fDB8fHww&auto=format&fit=crop&w=500&q=60",
          name: "Adele",
          rate: 4.5,
          message: "Barang nya bagus dan berfungsi normal, harus banget buat langganan disini!",
          date: "13-04-2023",
        },
      ]
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
            img: this.data.thumbnail,
            title: this.data.title,
            price: this.data.price,
            quantity: this.qty,
            stock: this.data.stock,
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
    openCartForm() {
      const form = document.querySelector(".cart-form")
      const txtPesan = document.querySelector(".pesan")
      const txtBatal = document.querySelector(".batal")
      txtPesan.classList.toggle("hidden")
      txtBatal.classList.toggle("hidden")
      form.classList.toggle("max-md:-bottom-64")
      form.classList.toggle("max-md:bottom-0")
    }
  },
  setup() {
    const onSwiper = (swiper) => {
      console.log(swiper);
    };
    const onSlideChange = () => {
      console.log('slide change');
    };
    return {
      onSwiper,
      onSlideChange,
      modules: [Navigation, Pagination]
    };
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