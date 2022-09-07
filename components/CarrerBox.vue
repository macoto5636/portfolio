<template>
  <div class="w-full bg-gray-100 rounded-lg p-5 md:p-10">
    <div class="font-bold text-gray-500 text-sm md:text-base">{{title}}</div>
    <div class="text-gray-500 mt-2 text-sm md:mx-5 md:mt-5 md:text-base">{{text}}</div>
  </div>
</template>

<script>
export default {
  props: ["title","text"]
}
</script>