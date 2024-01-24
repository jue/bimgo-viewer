<script setup>
const name = ref('World')
</script>

<template>
  <NuxtLink to="/designviews">
  <h1 class="text-3xl font-bold underline">
    Hello {{ name }}!
   </h1>
  </NuxtLink>
</template>
