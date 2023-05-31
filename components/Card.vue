<template>
  <div
    v-if="datas.length == 0"
    class="absolute flex justify-center w-full pt-28"
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
  <div
    v-else
    v-for="data in datas"
    :key="data.id"
    class="min-h-36 relative group cursor-pointer transition-all ease duration-300"
  >
    <NuxtLink
      :class="`w-full h-auto overflow-auto flex rounded-xl relative images${data.id} scroll-smooth image-wrapper`"
      :to="`/${data.id}`"
    >
      <img :src="data?.thumbnail" alt="" class="aspect-square object-cover" />
      <img
        v-for="images in data.images"
        :src="images"
        :key="images"
        alt=""
        class="aspect-square object-cover"
      />
    </NuxtLink>
    <NuxtLink class="mt-3 flex gap-x-2 justify-between" :to="`/${data.id}`">
      <div>
        <p class="font-semibold">{{ data.title }}</p>
        <p class="text-gray-600">{{ data.brand }}, {{ data.category }}</p>
        <p class="text-gray-600 -mt-1">{{ data.stock }} pcs</p>
        <p class="font-semibold">
          Rp {{ (data.price * 14987).toLocaleString("id-ID") }}
        </p>
      </div>
      <div>
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
              fill="#000"
            />
          </svg>
          <span>{{ data.rating }}</span>
        </p>
      </div>
    </NuxtLink>
    <div
      class="absolute w-[87%] left-0 md:top-[40%] top-[47%] h-0 hidden group-hover:flex justify-between items-center pl-8 transition-all ease duration-300"
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
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return { datas: [], category: null };
  },
  async created() {
    this.getDatas();
  },
  methods: {
    async getDatas() {
      try {
        const res = await axios.get("https://dummyjson.com/products");
        this.datas = await res.data.products;
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
  mounted() {
    this.category = this.$route.query.category;
  },
};
</script>

<style scope>
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
</style>
