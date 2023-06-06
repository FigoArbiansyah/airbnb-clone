<template>
  <div class="main-content">
    <ReservationNavbar />
    <slot />
  </div>
  <!-- TOTAL FIXED -->
  <div class="py-4 fixed bottom-0 bg-white w-full border-t px-4 z-50">
    <div class="flex justify-between font-semibold ">
      <p>Total (IDR)</p>
      <p>Rp. {{ total.toLocaleString() }}</p>
    </div>
    <div class="text-end mt-6">
      <a :href="`https://wa.me/+62895358905664?text=${message}`" class="py-2 px-4 bg-[#EF5A5F] hover:bg-[#FF5F5C] rounded-lg font-semibold text-white transition-all ease" target="_blank">Pesan Sekarang</a>
    </div>
  </div>
</template>