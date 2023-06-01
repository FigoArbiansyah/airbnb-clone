<template>
  <div></div>
</template>

<script setup>
onMounted(() => {
  if (process.client) {
    location.href = "/";
  }
});
</script>
