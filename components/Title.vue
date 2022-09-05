<template>
  <div class="pt-20 py-10">
    <p class="text-2xl text-gray-500 font-semibold text-center">
      {{title}}
    </p>
    <p class="mt-2 text-gray-500 text-center">
      - {{additional}} -
    </p>
  </div>
</template>

<script>
export default {
  props: ["title", "additional"]
}
</script>