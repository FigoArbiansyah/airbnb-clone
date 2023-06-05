<template>
  <header class="z-50 bg-white">
      <Navbar />
  </header>
  <main class="min-h-[80vh]">
      <section class="md:px-[150px] px-4 pt-10">
        <div class="relative">
            <div class="flex flex-col gap-y-6 mx-auto border border-[#ff5f5c] shadow-lg md:w-96 w-[80%] items-center py-6 pb-10 rounded relative bg-white bg-opacity-50 backdrop-blur z-50">
                <a :href="user?.image" target="_blank" class="w-48 aspect-square border overflow-hidden rounded-full">
                    <img :src="user?.image" class="w-full object-cover" alt="">
                </a>
                <div class="text-center">
                    <p class="font-light">{{ user?.username }}</p>
                    <div class="flex gap-x-1 items-center">
                        <h3 class="text-xl font-semibold">{{ `${user?.firstName} ${user?.lastName}` }}</h3>
                        <img v-if="user?.gender == 'male'" src="https://img.icons8.com/?size=512&id=12351&format=png" class="w-5 object-cover" alt="">
                        <img v-if="user?.gender == 'female'" src="https://img.icons8.com/?size=1x&id=12140&format=png" class="w-5 object-cover" alt="">
                    </div>
                    <p class="text-gray-500 italic mt-3">{{ user?.email }}</p>
                </div>
            </div>
            <div class=" md:w-32 aspect-square bg-[#ff5f5c] absolute bottom-[10%] left-[33%] -z-[100] rounded-full bola-1"></div>
            <div class=" md:w-32 aspect-square bg-[#ff5f5c] absolute -bottom-[5%] left-[30%] -z-[100] rounded"></div>
            <div class=" md:w-32 aspect-square bg-[#ff5f5c] absolute bottom-[68%] left-[57%] -z-[100] rounded"></div>
          </div>
      </section>
  </main>
</template>

<script>
export default {
    data () {
        return {
            user: ""
        }
    },
    mounted() {
        if (process.client) {
            const data = JSON.parse(localStorage.getItem("user")) || "";
            if (!data) {
                location.href = "/"
            } else {
                this.user = data;
            }
        }
    },
}
</script>

<style scope>
.bola-1 {
    animation: bola-1 45s ease infinite;
}
@keyframes bola-1 {
    0% {
        bottom: 10%;
        left: 33%;
    }
    25% {
        bottom: 35%;
        left: 55%;
        border-radius: 0%;
    }
    50% {
        bottom: 60%;
        left: 33%;
    }
    75% {
        bottom: 13%;
        left: 53%;
        border-radius: 50%;
    }
    100% {
        bottom: 10%;
        left: 33%;
    }
}
</style>