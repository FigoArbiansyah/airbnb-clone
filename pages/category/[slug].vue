<template>
  <main class="main-content">
    <TopNav />
    <Navbar />
    <div class="min-h-screen">
      <TotalPrice />
      <section
        class="relative mt-5 md:px-[38px] px-3 grid lg:grid-cols-4 md:grid-cols-2 grid-cols-1 gap-x-6 gap-y-10"
      >
        <Card :category="slug" />
      </section>
    </div>
  </main>
</template>

<script setup>
const route = useRoute();
const slug = route.params.slug;
</script>
