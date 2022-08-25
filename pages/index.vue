<template>
  <div>
    <div class="flex flex-wrap w-full items-center">
      <div class="w-1/3">
        <div class="h-full mr-10">
          <ul class="list-none space-y-8 text-right text-gray-500">
            <li>
              <a href="#responsive-header" class="text-teal-lighter hover:text-cyan-500">
                About me
              </a>
            </li>
            <li>
              <a href="#responsive-header" class="text-teal-lighter hover:text-cyan-500">
                Carrer
              </a>
            </li>
            <li>
              <a href="#responsive-header" class="text-teal-lighter hover:text-cyan-500">
                Skills
              </a>
            </li>
            <li>
              <a href="#responsive-header" class="text-teal-lighter hover:text-cyan-500">
                Works
              </a>
            </li>
            <li>
              <a href="#responsive-header" class="text-teal-lighter hover:text-cyan-500">
                Contact
              </a>
            </li>
          </ul>
        </div>
      </div>
      <img class="w-2/3 object-cover object-center" :src="settings.mainImagePC.url+'?w=2000'" alt="step" />
    </div>
    <div class="min-h-screen w-full mr-10 bg-gray-100">
      <div class="pt-20 py-10 text-2xl text-gray-500 font-bold text-center">
        About me
      </div>
    </div>
    <div class="min-h-screen grid grid-cols-3">
      <div class="mainVisual">
        <img
          :width="settings.mainImagePC.width"
          :height="settings.mainImagePC.height"
          :src="settings.mainImagePC.url+'?w=2000'"
          alt=""
        />
        <img
          :src="settings.profileImage.url+'?w=200'"
        />
        {{settings.name}}
      </div>
    </div>

    <!-- <Tutorial /> -->
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  async asyncData({ $microcms }) {
    const settings = await $microcms.get({
      endpoint: 'settings',
    })

    return {
      settings,
    }
  }
})
</script>
