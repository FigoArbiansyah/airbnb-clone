<template>
  <!-- TOTAL CARD -->
  <div class="lg:col-span-4 md:col-span-2 col-span-2">
    <div class="mt-3 flex justify-center">
      <div class="py-4 px-3 border rounded-xl flex items-center">
        <div class="flex max-md:flex-col">
          <p class="font-semibold pr-4 md:border-r border-gray-300">
            Tampilkan harga total
          </p>
          <p class="text-gray-500 md:pl-4">Termasuk semua biaya, setelah diskon</p>
        </div>
        <div
          class="ml-6 w-14 h-8 rounded-full bg-gray-400 bg-opacity-80 p-[1px] relative hover:bg-[#717171] cursor-pointer transition-all ease duration-300"
          @click="toggle()"
        >
          <div
            class="absolute top-[2px] left-[2px] w-7 h-7 bg-white rounded-full switch-button transition-all ease duration-300"
          ></div>
        </div>
      </div>
    </div>
  </div>
  <!-- LOADING SCREEN -->
  <div
    v-if="datas.length == 0 || !isShow"
    class="absolute flex justify-center w-full md:pt-28 pt-48"
  >
    <div class="sound-wave">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>
  <!-- CARD -->
  <NuxtLink
    v-else
    v-for="data in datas"
    :key="data.id"
    class="min-h-36 relative group transition-all ease duration-300"
    :to="`/products/${data.id}`"
  >
    <swiper
    direction="horizontal"
    :slides-per-view="1"
    navigation
    :pagination="{ clickable: false }"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
    :modules="modules"
      :class="`w-full md:rounded-xl relative images${data.id} scroll-smooth`"
    >
      <swiper-slide class="">
        <img :src="data?.thumbnail" alt="" class="aspect-square object-cover w-full image-products" />
      </swiper-slide>
      <swiper-slide class="" v-for="(images, i) in data.images">
        <img
          :key="i"
          :src="images"
          alt=""
          class="aspect-square object-cover w-full image-products"
        />
      </swiper-slide>
    </swiper>
    <NuxtLink class="mt-3 flex gap-x-2 justify-between max-md:flex-col max-md:px-2">
      <div>
        <div>
          <p class="font-semibold">{{ data.title }}</p>
          <p class="text-gray-600 max-md:hidden">{{ data.description.substring(0, 26) }}...</p>
          <p class="text-gray-600 md:hidden">{{ data.description.substring(0, 13) }}...</p>
        </div>
        <div>
          <p v-if="!discountPrice" class="font-semibold">
            Rp {{ (data.price * 14987).toLocaleString("id-ID") }}
          </p>
          <div v-if="discountPrice">
            <p class="line-through">
              Rp {{ (data.price * 14987).toLocaleString("id-ID") }}
            </p>
            <p class="font-semibold">
              Rp {{ ((data.price * 14987 - data.price * 14987 * (data.discountPercentage / 100)).toLocaleString("id-ID")).split(",")[0] }}
            </p>
          </div>
        </div>
      </div>
      <div class="max-md:flex justify-between items-center mt-1">
        <p class="flex gap-x-[3px] items-center">
          <svg
            width="14"
            height="14"
            viewBox="0 0 8 8"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M4 0L4.89806 2.76393H7.80423L5.45308 4.47214L6.35114 7.23607L4 5.52786L1.64886 7.23607L2.54692 4.47214L0.195774 2.76393H3.10194L4 0Z"
              fill="rgb(255, 238, 0)"
            />
          </svg>
          <span class="text-sm">{{ data.rating }}</span>
        </p>
        <p class="text-gray-600 md:mt-1 text-xs">{{ data.stock }} pcs</p>
      </div>
    </NuxtLink>
    <!-- <div
      class="absolute w-[87%] left-0 md:top-[40%] max-md:top-[30%] max-md:-translate-y-[30%] h-0 hidden group-hover:flex justify-between items-center pl-8 max-md:pr-4 transition-all ease duration-300"
    >
      <div class="relative h-full flex items-center">
        <button
          type="button"
          @click="scrollToPrev(data.id)"
          class="p-2 flex justify-center items-center bg-white border absolute top-[50%] -translate-y-[50%] rounded-full border-gray-300 hover:scale-[1.1] z-40 -left-6"
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
        </button>
      </div>
      <div class="relative h-full flex items-center">
        <button
          type="button"
          @click="scrollToNext(data.id)"
          class="p-2 flex justify-center items-center bg-white border absolute top-[50%] -translate-y-[50%] rounded-full border-gray-300 hover:scale-[1.1] z-40 -right-6"
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
              d="M8.25 4.5l7.5 7.5-7.5 7.5"
            />
          </svg>
        </button>
      </div>
    </div> -->
  </NuxtLink>
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
      datas: [], 
      route: useRoute(), 
      isShow: true, 
      discountPrice: false,
    };
  },
  props: ["category", "query"],
  async created() {
    this.getDatas();
  },
  methods: {
    async getDatas() {
      try {
        if (this.query == null && this.category == null) {
          const res = await axios.get("https://dummyjson.com/products");
          this.datas = await res.data.products;
        } else if (this.query != null && this.category == null) {
          const res = await axios.get(
            "https://dummyjson.com/products/search?q=" + this.query
          );
          this.datas = await res.data.products;
        } else if (this.query == null && this.category != null) {
          const res = await axios.get(
            "https://dummyjson.com/products/category/" + this.category
          );
          this.datas = await res.data.products;
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
    toggle () {
      document.querySelector(".switch-button").classList.toggle("left-[2px]");
      document.querySelector(".switch-button").classList.toggle("right-[2px]");
      this.isShow = !this.isShow
      setInterval(() => {
        this.isShow = true
      }, 500)
      this.discountPrice = !this.discountPrice
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

<style>
.image-wrapper {
  scroll-snap-type: x mandatory;
}
.image-wrapper::-webkit-scrollbar {
  display: none;
}
@keyframes audio-wave {
  0% {
    height: 10px;
    trnsform: translateY(0px);
    background: #ff55bb;
  }
  25% {
    height: 40px;
    trnsform: translateY(-5px) scaleY(1.7);
    background: #ffd3a3;
  }
  50% {
    height: 10px;
    trnsform: translateY(0px) scaleY(1.7);
    background: #fcffb2;
  }
  100% {
    height: 10px;
    trnsform: translateY(0px) scaleY(1.7);
    background: #b6eafa;
  }
}

.sound-wave {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 8px;
  height: 60px;
}
.sound-wave span {
  height: 18px;
  width: 10px;
  display: block;
  border-radius: 8px;
  background: orange;
  animation: audio-wave 2.2s infinite ease-in-out;
}
.sound-wave span:nth-child(2) {
  left: 11px;
  background: red;
  animation-delay: 0.2s;
}
.sound-wave span:nth-child(3) {
  left: 22px;
  animation-delay: 0.4s;
}
.sound-wave span:nth-child(4) {
  left: 33px;
  animation-delay: 0.6s;
}
.sound-wave span:nth-child(5) {
  left: 44px;
  animation-delay: 0.8s;
}
.sound-wave span:nth-child(6) {
  left: 55px;
  animation-delay: 1s;
}
.image-products {
  aspect-ratio: 1/1;
}
.swiper:hover .swiper-button-next, .swiper:hover .swiper-button-prev  {
  opacity: 1 !important;
}
.swiper:hover .swiper-button-disabled {
  opacity: 0.3 !important
}
.swiper-button-next, .swiper-button-prev {
  color: #ff5f5c !important;
  transform: scale(.6) !important;
  opacity: 0 !important;
  transition: all .3s ease;
}
.swiper-button-disabled {
  opacity: 0 !important
}
.swiper-button-next:hover, .swiper-button-prev:hover {
  transform: scale(.8) !important;
}
.swiper-pagination-bullet-active {
  background-color: #ff5f5c !important;
}
</style>
