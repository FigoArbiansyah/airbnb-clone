<template>
  <div class="main-content pb-20">
    <DetailNavbar />
    <div class="min-h-screen">
      <section
        v-for="data in filterCarts"
        class="relative p-5 md:px-[115px] px-3 border-t"
      >
        <div class="mt-3">
          <p class="text-lg font-semibold">{{ data?.title }}</p>
        </div>
        <div class="flex justify-between items-center mt-2 w-full">
          <div class="flex gap-2">
            <div class="">
              <p class="text-sm">
                Harga Awal:
                <span class="font-semibold">
                  Rp.
                  {{ (data.price * 14987).toLocaleString("id-ID") }}</span
                >
              </p>
              <p class="text-sm">
                diskon:
                <span class="font-semibold">
                  Rp.
                  {{
                    (
                      data.price *
                      14987 *
                      (data.discountPercentage / 100)
                    ).toLocaleString("id-ID")
                  }}</span
                >
              </p>
              <p class="text-sm">
                setelah diskon:
                <span class="font-semibold text-green-600"
                  >Rp.
                  {{
                    (
                      data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)
                    ).toLocaleString("id-ID")
                  }}</span
                >
              </p>
              <p class="text-sm">
                kuantitas:
                <span class="text-black"> {{ data.quantity }} pcs</span>
              </p>
              <p class="text-sm">
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
          <div class="flex gap-x-3">
            <button
              @click="
                selectButton(
                  data.id,
                  data.title,
                  data.price,
                  data.quantity,
                  data.total,
                  data.discountPercentage,
                  data.discountedPrice
                )
              "
              :class="`py-2 px-3 bg-gray-700 rounded-lg text-white pilih${data.id}`"
            >
              <p class="">Pilih</p>
            </button>
            <button
              @click="cancelButton(data.id)"
              :class="`py-2 px-3 bg-gray-700 rounded-lg text-white urungkan${data.id} hidden`"
            >
              <p class="">Urungkan</p>
            </button>
          </div>
        </div>
      </section>
      <section
        v-for="data in carts?.products"
        class="relative p-5 md:px-[115px] px-3 border-t"
      >
        <div class="mt-3">
          <p class="text-lg font-semibold">{{ data?.title }}</p>
        </div>
        <div class="flex justify-between items-center mt-2 w-full">
          <div class="flex gap-2">
            <div class="">
              <p class="text-sm">
                Harga Awal:
                <span class="font-semibold">
                  Rp.
                  {{ (data.price * 14987).toLocaleString("id-ID") }}</span
                >
              </p>
              <p class="text-sm">
                diskon:
                <span class="font-semibold">
                  Rp.
                  {{
                    (
                      data.price *
                      14987 *
                      (data.discountPercentage / 100)
                    ).toLocaleString("id-ID")
                  }}</span
                >
              </p>
              <p class="text-sm">
                setelah diskon:
                <span class="font-semibold text-green-600"
                  >Rp.
                  {{
                    (
                      data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)
                    ).toLocaleString("id-ID")
                  }}</span
                >
              </p>
              <p class="text-sm">
                kuantitas:
                <span class="text-black"> {{ data.quantity }} pcs</span>
              </p>
              <p class="text-sm">
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
          <div class="flex gap-x-3">
            <button
              @click="
                selectButton(
                  data.id,
                  data.title,
                  data.price,
                  data.quantity,
                  data.total,
                  data.discountPercentage,
                  data.discountedPrice
                )
              "
              :class="`py-2 px-3 bg-gray-700 rounded-lg text-white pilih${data.id}`"
            >
              <p class="">Pilih</p>
            </button>
            <button
              @click="cancelButton(data.id)"
              :class="`py-2 px-3 bg-gray-700 rounded-lg text-white urungkan${data.id} hidden`"
            >
              <p class="">Urungkan</p>
            </button>
          </div>
        </div>
      </section>
      <div class="text-center mt-6">
        <NuxtLink
          to="/reservation"
          class="py-3 px-10 bg-[#EF5A5F] hover:bg-[#FF5F5C] rounded-lg font-semibold text-white transition-all ease button-co"
          >Checkout</NuxtLink
        >
      </div>
      {{ user.id }}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      carts: [],
      localCarts: [],
      filterCarts:
        this.localCarts?.filter((p) => p.userId == this.user.id) || [],
      user: [],
    };
  },
  methods: {
    async getDataCarts() {
      try {
        const user = JSON.parse(localStorage.getItem("user"));
        const res = await axios.get(
          "https://dummyjson.com/carts/user/" + user.id
        );
        this.carts = await res.data.carts[0];
        console.log(res.data.carts);
      } catch (error) {
        console.log(error);
      }
    },
    selectButton(
      id,
      title,
      price,
      quantity,
      total,
      discountPercentage,
      discountedPrice
    ) {
      const newData = {
        id,
        title,
        price,
        quantity,
        total,
        discountPercentage,
        discountedPrice,
      };
      const products = JSON.parse(localStorage.getItem("products")) || [];
      products.push(newData);
      localStorage.setItem("products", JSON.stringify(products));
      document.querySelector(".urungkan" + id).classList.remove("hidden");
      document.querySelector(".pilih" + id).classList.add("hidden");
    },
    cancelButton(id) {
      const products = JSON.parse(localStorage.getItem("products"));
      const index = products.findIndex((product) => product.id === id);
      if (index !== -1) {
        products.splice(index, 1);
      }
      localStorage.setItem("products", JSON.stringify(products));
      document.querySelector(".pilih" + id).classList.remove("hidden");
      document.querySelector(".urungkan" + id).classList.add("hidden");
    },
  },
  async created() {
    this.getDataCarts();
  },
  mounted() {
    if (process.client) {
      localStorage.setItem("products", JSON.stringify([]));
      const datas = JSON.parse(localStorage.getItem("carts"));
      const user = JSON.parse(localStorage.getItem("user"));
      this.user = user;
      this.localCarts = datas;
      this.filterCarts = datas.filter((p) => p.userId == user.id);
    }
  },
};
</script>
