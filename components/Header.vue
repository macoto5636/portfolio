<template>
  <div class="sticky top-0 z-50 bg-white">
    <header class="header">
        <nav class="flex items-center justify-between flex-wrap p-6">
            <div class="flex items-center flex-no-shrink text-black mr-6">
                <span class="font-semibold text-xl tracking-tight">KITANO's Portfolio</span>
            </div>
            <div class="w-full block flex-grow lg:flex lg:items-center lg:w-auto">
                <div class="text-sm lg:flex-grow">
                <a href="#responsive-header" class="block mt-4 lg:inline-block lg:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                    About Us
                </a>
                <a href="#responsive-header" class="block mt-4 lg:inline-block lg:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                    Carrer
                </a>
                <a href="#responsive-header" class="block mt-4 lg:inline-block lg:mt-0 text-teal-lighter hover:text-cyan-500 mr-4">
                    Skills
                </a>
                <a href="#responsive-header" class="block mt-4 lg:inline-block lg:mt-0 text-teal-lighter hover:text-cyan-500">
                    Contact us
                </a>
                </div>
            </div>
        </nav>
    </header>
  </div>
</template>

<script>
export default {
  computed: {
    // TOPページかどうか
    isTopPage() {
      if (this.$route.name === 'index') return true
      return false
    },
  },
}
</script>