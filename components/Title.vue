<template>
  <div class="py-10 pt-20">
    <p class="text-center text-2xl font-semibold text-gray-500">
      {{ title }}
    </p>
    <p class="mt-2 text-center text-gray-500">- {{ additional }} -</p>
  </div>
</template>

<script>
export default {
  props: ['title', 'additional'],
}
</script>
