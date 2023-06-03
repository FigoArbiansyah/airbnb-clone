<template>
  <section class="min-h-screen flex justify-center items-center">
    <div class="md:w-[25rem] w-[70%] py-8 px-5 text-center border bg-white shadow-xl rounded-lg">
      <NuxtLink to="/" class="w-20 inline-block">
        <img src="~/assets/img/red-logo.svg" class="mx-auto w-20 h-20" alt="" />
      </NuxtLink>
      <div class="grid text-start gap-y-2 mt-10">
        <input
          type="text"
          class="py-2 px-3 outline-none border border-gray-200 focus:border-[#EF5A5F] rounded transition-all ease duration-300"
          v-model="username"
          placeholder="Username"
          required
        />
      </div>
      <div class="mt-3 grid text-start gap-y-2">
        <input
          type="password"
          class="py-2 px-3 outline-none border border-gray-200 focus:border-[#EF5A5F] rounded transition-all ease duration-300"
          v-model="password"
          placeholder="Password"
          required
        />
      </div>
      <div class="mt-6 flex justify-end items-center">
      <!-- <NuxtLink to="/" class="underline">Lewati</NuxtLink> -->
        <button
          @click="handleLogin()"
          class="py-2 px-5 bg-[#FF5F5C] hover:bg-[#EF5A5F] text-white rounded transition-all"
        >
          Sign In
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async handleLogin() {
      if (this.username == "" || this.password == "") {
        alert("Isi field dengan benar!")
      } else {
          try {
            await axios
            .post("https://dummyjson.com/auth/login", {
              username: this.username,
              password: this.password,
            })
            .then((res) => {
              localStorage.setItem("user", JSON.stringify(res.data));
              localStorage.setItem("id", JSON.stringify(res.data.id));
              alert("Berhasil login!");
              location.href = "/";
            });
          } catch (error) {
            if (error.message == "Request failed with status code 400") {
              alert("Data yang dimasukkan tidak valid!")
            } else {
              alert(error.message)
            }
          }
      }
    },
  },
};
</script>
