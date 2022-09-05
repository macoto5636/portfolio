<template>
  <div class="accordion">
    <ul>
      <li v-for="(work, index) in works" :key="work.id">
        <button type="button" class="accordion__toggle transition duration-300 ease-in-out hover:bg-gray-100" :class="{ 'is-active': isOpen[index] }" @click="handleToggle(index)">
          <div class="mx-5 mt-2 flex w-full">
            <img class="w-5 object-contain" :src="work.icon.url+'?w=50'" />
            <span v-text="work.name" class="ml-2 text-gray-500 font-semibold" />
            <span v-text="work.category" class="ml-5 text-gray-400" />
          </div>
        </button>
        <transition name="topSlide" @before-enter="beforeEnter" @enter="enter" @before-leave="beforeLeave" @leave="leave">
          <div v-show="isOpen[index]" class="topSlide my-3 flex w-full" >
            <img class="w-1/2 h-96 mx-5 object-contain" :src="work.image.url+'?w=500'" />
            <div class="w-1/2 my-3 text-gray-500">
              <table class="min-w-full">
                <tbody>
                  <tr class="border-b">
                    <td class="text-sm text-gray-500 font-light px-6 py-4 whitespace-nowrap">
                      使用技術
                    </td>
                    <td class="text-sm text-gray-500 font-light px-6 py-4">
                      {{work.tech}}
                    </td>
                  </tr>
                  <tr class="border-b">
                    <td class="text-sm text-gray-500 font-light px-6 py-4 whitespace-nowrap">
                      制作時期
                    </td>
                    <td class="text-sm text-gray-500 font-light px-6 py-4">
                      {{work.span}}
                    </td>
                  </tr>
                  <tr class="border-b">
                    <td class="text-sm text-gray-500 font-light px-6 py-4 whitespace-nowrap">
                      開発人数
                    </td>
                    <td class="text-sm text-gray-500 font-light px-6 py-4">
                      {{work.member}}
                    </td>
                  </tr>
                </tbody>
              </table>
              <div class="text-sm text-grya-500 m-5">
                テキストテキストテキストテキストテキストテキストテキストテキストテキストテキスト
              </div>
            </div>
          </div>
        </transition>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["works"],
  data() {
    return {
      isOpen: [],
    }
  },
  created() {
    this.isOpen = Array(this.works.length).fill(false)
    this.isOpen[0] = true
  },
  methods: {
    join(value) {
      if (!value) return ''
      return value.join(", ")
    },
    handleToggle(index) {
      if (!this.isOpen[index]) {
        this.isOpen = Array(this.works.length).fill(false)
      }
      this.isOpen.splice(index, 1, !this.isOpen[index])
      console.log(this.isOpen)
    },
    beforeEnter(el) {
      el.style.height = '0'
    },
    enter(el) {
      el.style.height = el.scrollHeight + 'px'
    },
    beforeLeave(el) {
       el.style.height = el.scrollHeight + 'px'
    },
    leave(el) {
      el.style.height = '0'
    },
  },
}
</script>