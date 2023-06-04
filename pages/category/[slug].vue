<template>
  <main class="main-content">
    <TopNav />
    <header class="z-50 bg-white md:sticky md:top-0">
      <Navbar>
        <Category />
      </Navbar>
    </header>
    <div class="min-h-screen">
      <!-- <TotalPrice /> -->
      <section
        class="relative mt-5 md:px-[38px] px-5 grid lg:grid-cols-4 md:grid-cols-2 grid-cols-2 gap-x-6 gap-y-10"
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
