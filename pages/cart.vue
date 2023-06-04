<template>
  <div class="main-content pb-20">
    <header class="z-50 bg-white">
      <Navbar />
    </header>
    <div class="">
      <section
        v-for="data in filterCarts"
        class="relative p-5 md:px-[115px] px-5 border-t"
      >
        <div class="mt-3 max-md:w-[100%]">
          <div class="flex gap-x-3 items-center">
            <p class="text-lg font-semibold">{{ data?.title }}</p>
            <div class="px-1 bg-[#FF5F5C] inline-block text-sm text-white rounded">{{ data.discountPercentage }}%</div>
          </div>
        </div>
        <div class="flex justify-between items-center mt-2 w-full gap-x-3">
          <div class="flex gap-2">
            <div class="">
              <p class="line-through">
                <span class="">
                  Rp.
                  {{ (data.price * 14987).toLocaleString("id-ID") }}</span
                >
              </p>
              <p class="">
                <span class="font-semibold text-green-600"
                  >Rp.
                  {{
                    (
                      data.price * 14987 -
                      data.price * 14987 * (data.discountPercentage / 100)
                    ).toLocaleString("id-ID").split(",")[0]
                  }}</span
                >
                <!-- <span class="text-gray-600 text-sm"> x {{ data.quantity }} pcs</span> -->
              </p>
              <!-- <p class="text-sm">
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
              </p> -->
              <div>
                <div class="flex items-center mt-3 justify-start">
                  <button class="p-2 text-xl cursor-pointer" @click="data.quantity -= 1" :disabled="data.quantity == 1 ? true : false">-</button>
                  <div class="w-12" v-if="data.quantity == 0 || data.quantity == 1 || data.quantity == ``">
                    <input type="number" value="1" class="pl-4 w-full">
                  </div>
                  <div class="w-12" v-else>
                    <input type="number" v-model="data.quantity" class="pl-4 w-full">
                  </div>
                  <div class="p-2 text-xl cursor-pointer" @click="data.quantity += 1">+</div>
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
                    :class="`relative p-1 rounded-lg hover:text-white pilih${data.id} transition-all ease duration-300`"
                  >
                    <p class="p-1 grid place-items-center relative -z-10">
                      <input type="checkbox" name="" class="w-5 h-5">
                    </p>
                  </button>
                  <button
                    @click="cancelButton(data.id)"
                    :class="`relative p-1 rounded-lg hover:text-white urungkan${data.id} hidden transition-all ease duration-300`"
                  >
                    <p class="p-1 grid place-items-center relative -z-10">
                      <input type="checkbox" name="" class="w-5 h-5" checked>
                    </p>
                  </button>
                  <button
                    @click="deleteButton(data.id)"
                    :class="`py-1 px-3 border border-[#FF5F5C] rounded-lg text-[#FF5F5C] hover:bg-[#FF5F5C] hover:text-white hapus${data.id} transition-all ease duration-300`"
                  >
                    <p class="">Hapus</p>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
  <div class="text-center w-full flex justify-end max-md:justify-between fixed bottom-0 pt-3 py-4 md:px-[115px] px-5 gap-x-4 items-center bg-white border-t">
  <p class="font-semibold md:text-xl">Rp. {{totalPriceAtCart.toLocaleString("id-ID").split(",")[0]}}</p>
    <NuxtLink
      to="/reservation"
      class="py-3 px-10 bg-[#EF5A5F] hover:bg-[#FF5F5C] rounded-lg font-semibold text-white transition-all ease button-co"
      >Checkout</NuxtLink
    >
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
      totalPriceAtCart: 0,
      historySelected: []
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
      const totalPrice = ((price * 14987 - price * 14987 * (discountPercentage / 100)) * quantity)
      this.historySelected.push({id: id, total:totalPrice})
      this.totalPriceAtCart = this.historySelected.reduce((acc, obj) => acc + obj.total, 0);
    },
    cancelButton(id, price) {
      const selectedData = this.historySelected.filter((data) => data.id != id)
      const notSelectedData = this.historySelected.filter((data) => data.id == id)[0]
      this.historySelected = selectedData
      this.totalPriceAtCart -= notSelectedData.total
      const products = JSON.parse(localStorage.getItem("products"));
      const index = products.findIndex((product) => product.id === id);
      if (index !== -1) {
        products.splice(index, 1);
      }
      localStorage.setItem("products", JSON.stringify(products));
      document.querySelector(".pilih" + id).classList.remove("hidden");
      document.querySelector(".urungkan" + id).classList.add("hidden");
    },
    deleteButton(id) {
      // const products = JSON.parse(localStorage.getItem("products"));
      // const selectedData = products.filter((data) => data.id != id)
      // localStorage.setItem("products", JSON.stringify([]))
      // products.push(selectedData)
      // localStorage.setItem("products", JSON.stringify(selectedData))
      alert("Fitur belum dijalankan")
    },
    handlePlus(qty) {
      return qty += 1
    },
    handleMinus(qty) {
      return qty -= 1
    }
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
