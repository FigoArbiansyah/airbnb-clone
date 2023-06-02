<template>
  <section class="min-h-screen flex justify-center items-center">
    <div class="md:w-[30rem] w-[90%] p-5 text-center">
      <h2 class="text-2xl font-semibold">Login</h2>
      <div class="mt-3 grid text-start gap-y-2">
        <label for="">Username</label>
        <input
          type="text"
          class="py-2 px-3 outline-none border border-gray-400 rounded"
          v-model="username"
          required
        />
      </div>
      <div class="mt-3 grid text-start gap-y-2">
        <label for="">Password</label>
        <input
          type="password"
          class="py-2 px-3 outline-none border border-gray-400 rounded"
          v-model="password"
          required
        />
      </div>
      <div class="mt-3 grid text-end gap-y-2">
        <button
          @click="handleLogin()"
          class="py-3 px-5 bg-black text-white rounded"
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
    },
  },
};
</script>
