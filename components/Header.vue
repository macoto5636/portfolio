<template>
  <transition>
    <div v-show="isShow" id="header" class="sticky top-0 z-50 bg-white">
      <header class="header">
        <nav class="flex items-center justify-between flex-wrap p-6">
          <div class="flex items-center flex-no-shrink text-black mr-6">
            <nuxt-link v-scroll-to="'#top'" to class="font-semibold text-lg tracking-tight">
              NOKITA's Portfolio
            </nuxt-link>
          </div>  
            <div class="w-full block flex-grow md:flex md:items-center md:w-auto">
              <div class="text-sm md:flex-grow">
                <nuxt-link v-scroll-to="'#about_me'" to class="block mt-4 mr-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500">
                  About me
                </nuxt-link>
                <nuxt-link v-scroll-to="'#carrer'" to class="block mt-4 mr-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500">
                  Carrer
                </nuxt-link>
                <nuxt-link v-scroll-to="'#skills'" to class="block mt-4 mr-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500">
                  Skills
                </nuxt-link>
                <nuxt-link v-scroll-to="'#works'" to class="block mt-4 mr-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500">
                  Works
                </nuxt-link>
                <nuxt-link v-scroll-to="'#contact_me'" to class="block mt-4 mr-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500">
                  Contact me
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
  data () {
    return {
      scrollY: 0,
      isShow: true
    }
  },
  mounted () {
    // スクロールイベントを取得
    window.addEventListener('scroll', this.onScroll)
    window.addEventListener('load', () => {
      this.onScroll()
    })
  },
  watch: {
    scrollY (newValue) {
      this.$set(this, 'isShow', newValue > window.innerHeight)
    }
  },
  methods: {
    onScroll () {
      this.$set(this, 'scrollY', window.pageYOffset)
    }
  }
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