<template>
  <transition>
    <div v-show="isShow" id="header" class="sticky top-0 z-50 bg-white">
      <header class="header">
        <nav class="flex items-center justify-between flex-wrap p-6">
          <div class="flex items-center flex-no-shrink text-black mr-6">
            <span class="font-semibold text-lg tracking-tight">KITANO's Portfolio</span>
          </div>  
            <div class="w-full block flex-grow md:flex md:items-center md:w-auto">
              <div class="text-sm md:flex-grow">
                <a href="#responsive-header" class="block mt-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                  About me
                </a>
                <a href="#responsive-header" class="block mt-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                  Carrer
                </a>
                <a href="#responsive-header" class="block mt-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                  Skills
                </a>
                <a href="#responsive-header" class="block mt-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                  Works
                </a>
                <a href="#responsive-header" class="block mt-4 text-gray-500 md:inline-block md:mt-0 text-teal-lighter hover:text-cyan-500">
                  Contact me
                </a>
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