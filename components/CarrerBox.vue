<template>
  <div class="w-full rounded-lg bg-gray-100 p-5 md:p-10">
    <div class="text-sm font-bold text-gray-500 md:text-base">{{ title }}</div>
    <div class="mt-2 text-sm text-gray-500 md:mx-5 md:mt-5 md:text-base">
      {{ text }}
    </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'text'],
}
</script>
