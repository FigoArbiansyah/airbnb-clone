<template>
  <main class="main-content">
    <TopNav />
    <header class="z-50 bg-white md:sticky md:top-0">
      <Navbar>
        <Category />
      </Navbar>
    </header>
    <div class="min-h-screen">
      <section
        class="relative mt-5 md:px-[38px] px-5 grid lg:grid-cols-4 md:grid-cols-2 grid-cols-1 gap-x-6 gap-y-10"
      >
        <Card :category="null" />
      </section>
    </div>
  </main>
</template>

<script setup>
useHead({
  title: "Gocommerce",
});
onMounted(() => {
  if (process.client) {
    const data = JSON.parse(localStorage.getItem("user")) || "0";
    if (data == "0") {
      localStorage.setItem("user", "0");
    }
  }
});
</script>
