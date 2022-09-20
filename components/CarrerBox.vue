<template>
  <div class="w-full rounded-lg bg-gray-100 p-5 md:p-10">
    <div class="text-sm font-bold text-gray-500 md:text-base">
      {{ title }}
      <span class="ml-3 inline md:hidden">({{ period }})</span>
    </div>
    <div v-html="text" class="mt-2 text-sm text-gray-500 md:mx-5 md:mt-5"></div>
    <div v-show="image" class="mt-3 flex flex-wrap md:mt-5 md:ml-5">
      <div class="w-full md:w-1/2">
        <img
          class="m-auto w-full object-cover object-center"
          :src="(image ? image.url : '') + '?w=500'"
        />
      </div>
      <div class="w-full pt-2 md:w-1/2 md:px-5">
        <div v-html="imageText" class="text-sm text-gray-500"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'text', 'period', 'image', 'imageText'],
}
</script>
