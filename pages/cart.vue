<template>
  <div class="main-content pb-20">
    <header class="z-50 bg-white">
      <Navbar />
    </header>
    <div class="">
      <section
        v-for="data in filterCarts"
        class="relative p-5 md:px-[115px] px-5 border-t flex gap-x-3"
      >
        <div class="w-28 mt-1">
          <img :src="data.img" class="w-full aspect-square object-cover" alt="">
        </div>
        <div>  
          <div class="max-md:w-[100%]">
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
                </p>
                <div>
                  <div class="flex items-center mt-3 justify-start">
                    <button class="p-2 text-xl cursor-pointer" @click="data.quantity -= 1; changeQty(
                          data.id,
                          data.title,
                          data.price,
                          data.quantity,
                          data.total,
                          data.discountPercentage,
                          data.discountedPrice
                        )" :disabled="data.quantity == 1 ? true : false">-</button>
                    <div class="w-12">
                      <p class="pl-4 w-full">{{data.quantity}}</p>
                    </div>
                    <div :class="`p-2 text-xl cursor-pointer ${data.quantity >= data.stock ? 'hidden' : 'inline'}`" @click="data.quantity += 1; changeQty(
                          data.id,
                          data.title,
                          data.price,
                          data.quantity,
                          data.total,
                          data.discountPercentage,
                          data.discountedPrice
                        )">+</div>
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
        </div>
      </section>
    </div>
  </div>
  <div class="text-center w-full flex justify-end max-md:justify-between fixed bottom-0 pt-3 py-4 md:px-[115px] px-5 gap-x-4 items-center bg-white border-t">
  <p v-if="!Number(totalPriceAtCart)" class="font-semibold md:text-xl">Rp. 0</p>
  <p v-if="Number(totalPriceAtCart)" class="font-semibold md:text-xl">Rp. {{totalPriceAtCart.toLocaleString("id-ID").split(",")[0]}}</p>
    <div
      v-if="totalPriceAtCart == 0"
      class="py-3 px-10 bg-[#EF5A5F] rounded-lg font-semibold text-white transition-all ease button-co bg-opacity-75 cursor-pointer"
      >Checkout</div
    >
    <NuxtLink
      v-else
      to="/summary"
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
      this.historySelected.push({id: id, quantity, total:totalPrice})
      this.totalPriceAtCart = this.historySelected.reduce((acc, obj) => acc + obj.total, 0);
    },
    cancelButton(id, price) {
      const selectedData = this.historySelected.filter((data) => data.id != id)
      const notSelectedData = this.historySelected.filter((data) => data.id == id)[0]
      this.historySelected = selectedData
      this.totalPriceAtCart -= notSelectedData?.total
      const products = JSON.parse(localStorage.getItem("products"));
      const index = products.findIndex((product) => product.id === id);
      if (index !== -1) {
        products.splice(index, 1);
      }
      localStorage.setItem("products", JSON.stringify(products));
      document.querySelector(".pilih" + id).classList.remove("hidden");
      document.querySelector(".urungkan" + id).classList.add("hidden");
    },
    changeQty(
      id,
      title,
      price,
      quantity,
      total,
      discountPercentage,
      discountedPrice
    ) {
      document.querySelector(".urungkan" + id).classList.remove("hidden");
      document.querySelector(".pilih" + id).classList.add("hidden");
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
      const totalPriceWithOutQty = (price * 14987 - price * 14987 * (discountPercentage / 100))
      const isAvailable = this.historySelected.some(item => item.id == id)
      if (isAvailable) {
        const oldData = this.historySelected.filter(item => item.id != id)
        const changedData = this.historySelected.filter(item => item.id == id)
        console.log(changedData)
        for (let i = 0; i < this.historySelected.length; i++) {
          if (id == this.historySelected[i].id) {
            this.historySelected[i].title = title
            this.historySelected[i].quantity += quantity
            this.historySelected[i].quantity = quantity
            this.historySelected[i].price = price
            this.historySelected[i].discountPercentage = discountPercentage
            const total = ((this.historySelected[i].price * 14987 - this.historySelected[i].price * 14987 * (this.historySelected[i].discountPercentage / 100)) * this.historySelected[i].quantity)
            this.historySelected[i].total = total
            this.historySelected[i].discountedPrice = discountedPrice
            // this.historySelected[i].quantity += quantity
            // this.historySelected[i].quantity = quantity
            const newQty = this.historySelected[i].quantity = quantity
            // const total = totalPriceWithOutQty * newQty
            // this.historySelected[i].total = total
            this.totalPriceAtCart = this.historySelected.reduce((acc, obj) => acc + obj.total, 0);
            // this.historySelected.push({id: this.historySelected[i].id, quantity: this.historySelected[i].quantity, total:totalPriceWithOutQty * this.historySelected[i].quantity})
            const notSelectedData = this.historySelected.filter(item => item.id != this.historySelected[i].id)
            // this.historySelected = notSelectedData
            localStorage.setItem("products", JSON.stringify(notSelectedData))
            if (notSelectedData.length == 0) {
              localStorage.setItem("products", JSON.stringify([this.historySelected[i]]))
            } else {
              localStorage.setItem("products", JSON.stringify(notSelectedData))
              const data = JSON.parse(localStorage.getItem("products"))
              data.push(this.historySelected[i])
              localStorage.setItem("products", JSON.stringify(data))
            }
          }
        } 
      } else {
        this.historySelected.push({id: id, quantity, total:totalPriceWithOutQty * quantity})
        console.log(isAvailable)
        this.totalPriceAtCart = this.historySelected.reduce((acc, obj) => acc + obj.total, 0);
      }
    },
    deleteButton(id) {
      this.cancelButton(id)
      const user = JSON.parse(localStorage.getItem("user"));
      const carts = JSON.parse(localStorage.getItem("carts"))
      localStorage.setItem("carts", JSON.stringify([]))
      const datas = carts.filter((data) => !(data.id == id && data.userId == user.id));
      localStorage.setItem("carts", JSON.stringify(datas))
      this.filterCarts = datas.filter((p) => p.userId == user.id);
      console.log(datas)
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
