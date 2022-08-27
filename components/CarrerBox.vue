<template>
  <div class="w-full bg-gray-100 rounded-lg p-10">
    <div class="font-bold text-gray-500">{{title}}</div>
    <div class="text-gray-500 mx-5 mt-5">{{text}}</div>
  </div>
</template>

<script>
export default {
  props: ["title","text"]
}
</script>