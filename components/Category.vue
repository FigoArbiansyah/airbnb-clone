<template>
  <nav
    class="pt-6 max-md:pb-2 px-[35px] relative flex max-md:flex-col justify-around gap-x-3 nav-category transition-all ease max-md:sticky top-0"
  >
    <div
      class="overflow-x-auto grid grid-flow-col auto-cols-max gap-x-8 scroll-category z-40 relative scroll-smooth md:w-[80%] w-full"
    >
      <NuxtLink
        v-for="category in categories"
        :to="`/category/${category}`"
        class="flex flex-col category-item items-center gap-y-2 text-sm pb-3 opacity-75 hover:opacity-100 hover:border-b-2 hover:border-gray-200 border-b-2 border-white transition-all ease cursor-pointer relative"
      >
        <img
          src="https://a0.muscache.com/pictures/7630c83f-96a8-4232-9a10-0398661e2e6f.jpg"
          alt=""
          class="w-6 h-6"
        />
        <p>{{ category }}</p>
      </NuxtLink>
    </div>
    <NuxtLink
      to="/"
      class="max-md:hidden p-2 border rounded-xl text-sm relative w-auto h-12 flex gap-x-2 justify-between items-center cursor-pointer max-md:z-50"
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
          d="M10.5 6h9.75M10.5 6a1.5 1.5 0 11-3 0m3 0a1.5 1.5 0 10-3 0M3.75 6H7.5m3 12h9.75m-9.75 0a1.5 1.5 0 01-3 0m3 0a1.5 1.5 0 00-3 0m-3.75 0H7.5m9-6h3.75m-3.75 0a1.5 1.5 0 01-3 0m3 0a1.5 1.5 0 00-3 0m-9.75 0h9.75"
        />
      </svg>
      <p>Filter</p>
    </NuxtLink>
    <div
      class="swipe-buttons absolute md:w-[87%] w-full left-0 top-0 h-full flex justify-between md:items-center md:pl-8 max-md:px-4"
    >
      <div class="relative h-full flex items-center btn-prev">
        <button
          type="button"
          @click="scrollToPrev()"
          class="p-2 flex justify-center items-center bg-white border relative rounded-full border-gray-300 hover:scale-[1.1] z-50"
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
      <div class="relative h-full flex items-center btn-next">
        <button
          type="button"
          @click="scrollToNext()"
          class="p-2 flex justify-center items-center bg-white border relative rounded-full border-gray-300 hover:scale-[1.1] z-50"
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
  </nav>
</template>

<script setup>
import axios from "axios";

let categories = [];

const getCategories = async () => {
  try {
    const res = await axios.get("https://dummyjson.com/products/categories");
    return res.data;
  } catch (error) {
    console.log(error);
  }
};

categories = await getCategories();

function scrollToNext() {
  const scrollCategory = document.querySelector(".scroll-category");
  scrollCategory.scrollLeft += scrollCategory.offsetWidth / 4;
}
function scrollToPrev() {
  const scrollCategory = document.querySelector(".scroll-category");
  scrollCategory.scrollLeft -= scrollCategory.offsetWidth / 4;
}

onMounted(() => {
  const navScroll = () => {
    const nav = document.querySelector(".nav-category");
    if (
      document.documentElement.scrollTop > 175 ||
      document.body.scrollTop > 175
    ) {
      nav.classList.add("border-b");
      nav.classList.add("shadow-sm");
    } else {
      nav.classList.remove("border-b");
      nav.classList.remove("shadow-sm");
    }
    window.addEventListener("scroll", navScroll);
  };
  navScroll();
  if (process.client) {
  }
});
</script>

<style scope>
.scroll-category::-webkit-scrollbar {
  display: none;
}
</style>
