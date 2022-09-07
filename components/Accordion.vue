<template>
  <div class="accordion">
    <ul>
      <li v-for="(work, index) in works" :key="work.id">
        <button
          type="button"
          class="accordion__toggle transition duration-300 ease-in-out hover:bg-gray-100"
          :class="{ 'is-active': isOpen[index] }"
          @click="handleToggle(index)"
        >
          <div class="mx-5 mt-2 flex w-full">
            <img class="w-5 object-contain" :src="work.icon.url + '?w=50'" />
            <span v-text="work.name" class="ml-2 font-semibold text-gray-500" />
            <span v-text="work.category" class="ml-5 text-gray-400" />
          </div>
        </button>
        <transition
          name="topSlide"
          @before-enter="beforeEnter"
          @enter="enter"
          @before-leave="beforeLeave"
          @leave="leave"
        >
          <div
            v-show="isOpen[index]"
            class="topSlide my-3 flex w-full flex-wrap"
          >
            <img
              class="w-full object-contain px-3 md:w-1/2"
              :src="work.image.url + '?w=500'"
            />
            <div class="my-3 w-full px-5 text-gray-500 md:w-1/2">
              <table class="min-w-full">
                <tbody>
                  <tr class="border-b">
                    <td class="whitespace-nowrap px-6 py-4 text-sm font-light">
                      使用技術
                    </td>
                    <td class="px-6 py-4 text-sm font-light">
                      {{ work.tech }}
                    </td>
                  </tr>
                  <tr class="border-b">
                    <td class="whitespace-nowrap px-6 py-4 text-sm font-light">
                      制作時期
                    </td>
                    <td class="px-6 py-4 text-sm font-light">
                      {{ work.span }}
                    </td>
                  </tr>
                  <tr class="border-b">
                    <td class="whitespace-nowrap px-6 py-4 text-sm font-light">
                      開発人数
                    </td>
                    <td class="px-6 py-4 text-sm font-light">
                      {{ work.member }}
                    </td>
                  </tr>
                </tbody>
              </table>
              <div class="m-5 text-sm">
                {{ work.content }}
              </div>
              <div class="md:m5 mx-5 my-2 flex">
                <a v-show="work.github1" :href="work.github1" target="_blank">
                  <img class="mr-2 w-6" src="@/assets/image/icon/github.png" />
                </a>
                <a v-show="work.github2" :href="work.github2" target="_blank">
                  <img class="mr-2 w-6" src="@/assets/image/icon/github.png" />
                </a>
                <a v-show="work.document" :href="work.document" target="_blank">
                  <img
                    class="mr-2 w-6"
                    src="@/assets/image/icon/whitebord.png"
                  />
                </a>
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
  props: ['works'],
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
    handleToggle(index) {
      if (!this.isOpen[index]) {
        this.isOpen = Array(this.works.length).fill(false)
      }
      this.isOpen.splice(index, 1, !this.isOpen[index])
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

<style lang="scss">
.accordion {
  width: 100%;
  top: 67px;
  left: 0;
  overflow: scroll;
  padding: 36px 16px;
}

.accordion__toggle {
  line-height: 2.818;
  display: block;
  width: 100%;
  border-bottom: 1px solid #ebebeb;
  position: relative;

  &::before,
  &::after {
    content: '';
    display: inline-block;
    width: 18px;
    height: 3px;
    background-color: #6b7280;
    position: absolute;
    top: 50%;
    right: 22px;
  }

  &::before {
    transform: translate(0, -50%);
  }

  &::after {
    transition: all 0.3s ease-in-out;
    transform: translate(0, -50%) rotate(90deg);
  }

  &.is-active {
    &::after {
      transform: translate(0, -50%) rotate(0deg);
    }
  }
}

.topSlide {
  transition: height 0.3s ease-in-out;
  overflow: hidden;
}

.topSlide-enter-active {
  animation-duration: 0.3s;
  animation-fill-mode: both;
}

.topSlide-leave-active {
  animation-duration: 0.3s;
  animation-fill-mode: both;
}
</style>
