<template>
  <transition>
    <div v-show="isShow" id="header" class="sticky top-0 z-50 bg-white">
      <header class="header">
        <nav class="flex flex-wrap items-center justify-between p-3 md:p-6">
          <div class="flex-no-shrink mr-6 flex items-center text-black">
            <nuxt-link
              v-scroll-to="'#top'"
              to
              class="text-lg font-semibold tracking-tight"
            >
              NOKITA's Portfolio
            </nuxt-link>
          </div>
          <div
            class="block hidden w-full w-auto flex-grow items-center md:flex"
          >
            <div class="text-sm">
              <nuxt-link
                v-scroll-to="'#about_me'"
                to
                class="text-teal-lighter mt-4 mr-4 block text-gray-500 hover:text-cyan-500 md:mt-0 md:inline-block"
              >
                About me
              </nuxt-link>
              <nuxt-link
                v-scroll-to="'#carrer'"
                to
                class="text-teal-lighter mt-4 mr-4 block text-gray-500 hover:text-cyan-500 md:mt-0 md:inline-block"
              >
                Carrer
              </nuxt-link>
              <nuxt-link
                v-scroll-to="'#skills'"
                to
                class="text-teal-lighter mt-4 mr-4 block text-gray-500 hover:text-cyan-500 md:mt-0 md:inline-block"
              >
                Skills
              </nuxt-link>
              <nuxt-link
                v-scroll-to="'#works'"
                to
                class="text-teal-lighter mt-4 mr-4 block text-gray-500 hover:text-cyan-500 md:mt-0 md:inline-block"
              >
                Works
              </nuxt-link>
              <nuxt-link
                v-scroll-to="'#contact_me'"
                to
                class="text-teal-lighter mt-4 mr-4 block text-gray-500 hover:text-cyan-500 md:mt-0 md:inline-block"
              >
                Contact
              </nuxt-link>
            </div>
          </div>
        </nav>
      </header>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      scrollY: 0,
      isShow: true,
    }
  },
  mounted() {
    // スクロールイベントを取得
    window.addEventListener('scroll', this.onScroll)
    window.addEventListener('load', () => {
      this.onScroll()
    })
  },
  watch: {
    scrollY(newValue) {
      this.$set(this, 'isShow', newValue > window.innerHeight)
    },
  },
  methods: {
    onScroll() {
      this.$set(this, 'scrollY', window.pageYOffset)
    },
  },
}
</script>

<style>
.v-leave-active,
.v-enter-active {
  transition: opacity 0.3s;
}

.v-enter,
.v-leave-to {
  opacity: 0;
}
</style>
