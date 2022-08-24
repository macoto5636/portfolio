<template>
  <div>
    <div class="min-h-screen grid grid-cols-3">
      <div className="col-span-1">1</div>
      <div className="col-span-2">2</div>
    </div>

    <!-- <Tutorial /> -->
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Header from '~/components/Header.vue'

export default Vue.extend({
  components: { Header },
  name: 'IndexPage',
  // async asyncData({ $microcms }) {
  //   const data = await $microcms.get({
  //     endpoint: 'work',
  //   })
  //   return {
  //     lists: data.contents,
  //   }
  // },
})
</script>
