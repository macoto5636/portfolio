<template>
  <div>
    <div
      id="top"
      class="flex min-h-screen w-full flex-row-reverse items-center md:flex-row"
    >
      <div class="w-1/2 pr-5 md:w-1/3 md:pr-10">
        <p class="text-right text-lg font-semibold tracking-tight">
          NOKITA's Portfolio
        </p>
        <ul class="mt-8 mb-5 list-none space-y-5 text-right text-gray-500">
          <li>
            <nuxt-link
              v-scroll-to="'#about_me'"
              to
              class="text-teal-lighter hover:text-cyan-500"
            >
              About me
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              v-scroll-to="'#carrer'"
              to
              class="text-teal-lighter hover:text-cyan-500"
            >
              Carrer
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              v-scroll-to="'#skills'"
              to
              class="text-teal-lighter hover:text-cyan-500"
            >
              Skills
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              v-scroll-to="'#works'"
              to
              class="text-teal-lighter hover:text-cyan-500"
            >
              Works
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              v-scroll-to="'#contact_me'"
              to
              class="text-teal-lighter hover:text-cyan-500"
            >
              Contact
            </nuxt-link>
          </li>
        </ul>
      </div>
      <div class="w-1/2 md:w-2/3">
        <img
          class="min-h-screen object-cover"
          :src="settings.mainImagePC.url + '?w=2000'"
          alt="top"
        />
      </div>
    </div>
    <div id="about_me" ref="about_me" class="w-full bg-gray-100 pb-8 md:pb-20">
      <Title title="About me" additional="自己紹介"></Title>
      <div class="mx-auto w-5/6 rounded-lg bg-gray-200 py-8 md:w-2/3 md:py-10">
        <div class="flex flex-wrap items-center">
          <div class="w-full md:w-1/2">
            <div>
              <img
                class="m-auto w-48 rounded-full object-cover object-center"
                :src="settings.profileImage.url + '?w=300'"
                alt="profile"
              />
            </div>
          </div>
          <div class="w-full p-5 md:w-1/2 md:pr-20">
            <p class="text-base font-bold text-gray-500 md:text-lg">
              {{ settings.name }}
            </p>
            <p class="my-3 text-sm text-gray-500 md:my-5 md:text-base">
              {{ birthday }}
            </p>
            <div
              v-html="settings.selfIntroduction"
              class="text-sm text-gray-500 md:text-base"
            ></div>
            <div class="mx-1 my-5 flex">
              <a
                :href="'https://github.com/' + settings.githubAccount"
                target="_blank"
              >
                <img class="w-6" src="@/assets/image/icon/github.png" />
              </a>
              <a
                :href="'https://twitter.com/' + settings.twitterAccount"
                target="_blank"
              >
                <img
                  class="my-1 mx-3 w-6"
                  src="@/assets/image/icon/twitter.svg"
                />
              </a>
              <a
                :href="'https://qiita.com/' + settings.qiitaAccount"
                target="_blank"
              >
                <img class="w-6" src="@/assets/image/icon/qiita.png" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div id="carrer" class="mr-10 w-full">
      <Title title="Carrer" additional="これまでとこれから"></Title>
      <div class="career mx-auto mb-20 md:w-2/3">
        <dl>
          <template v-for="carrer in carrers.contents">
            <dt :key="carrer.period">
              <div class="text-sm text-gray-500 md:text-base">
                {{ carrer.period }}
              </div>
            </dt>
            <dd :key="carrer.title">
              <CarrerBox
                :title="carrer.title"
                :text="carrer.text"
                :image="carrer.image"
                :imageText="carrer.imageText"
              ></CarrerBox>
            </dd>
          </template>
        </dl>
      </div>
    </div>
    <div id="skills" class="min-h-screen w-full bg-gray-100">
      <Title title="Skills" additional="スキルシート"></Title>
      <div class="mx-10 pb-5 md:mx-auto md:w-2/3 md:pb-20">
        <p class="text-base font-bold text-gray-500 md:text-lg">▶ 技術</p>
        <p class="mt-3 text-center text-xs text-gray-500 md:mx-12 md:text-sm">
          習熟度目安　★：ちょっとさわった　★★：調べながらであれば独力で使える　★★★：プロ
        </p>
        <div class="mt-5 mb-8 md:mx-12">
          <table class="min-w-full">
            <thead class="border-b">
              <tr>
                <th
                  scope="col"
                  class="p-2 text-left text-xs text-gray-500 md:px-6 md:py-4 md:text-sm"
                >
                  カテゴリ
                </th>
                <th
                  scope="col"
                  class="p-2 text-left text-xs text-gray-500 md:px-6 md:py-4 md:text-sm"
                >
                  技術名
                </th>
                <th
                  scope="col"
                  class="p-2 text-left text-xs text-gray-500 md:px-6 md:py-4 md:text-sm"
                >
                  習熟度
                </th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="skill in skills"
                :key="skill.name"
                class="border-b transition duration-300 ease-in-out hover:bg-gray-200"
              >
                <td
                  class="whitespace-nowrap p-2 text-xs font-light text-gray-600 md:px-6 md:py-4 md:text-sm"
                >
                  {{ skill.category }}
                </td>
                <td
                  class="whitespace-nowrap p-2 text-xs font-light text-gray-600 md:px-6 md:py-4 md:text-sm"
                >
                  {{ skill.name }}
                </td>
                <td
                  class="whitespace-nowrap p-2 text-xs font-light text-gray-600 md:px-6 md:py-4 md:text-sm"
                >
                  {{ skill.level | levelToStar }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <p class="text-base font-bold text-gray-500 md:text-lg">▶ 資格</p>
        <ul
          class="mx-12 mt-3 list-disc space-y-2 text-sm text-gray-500 md:text-base"
        >
          <li v-for="exam in exams" :key="exam">
            {{ exam }}
          </li>
        </ul>
      </div>
    </div>
    <div id="works" class="mr-10 w-full">
      <Title title="Works" additional="成果物"></Title>
      <div class="mx-auto w-full pb-5 md:w-2/3 md:pb-20">
        <Accordion :works="works.contents"></Accordion>
      </div>
    </div>
    <div id="contact_me" class="w-full bg-gray-100">
      <Title title="Contact" additional="連絡先"></Title>
      <div class="mx-auto w-2/3 pb-20">
        <div class="space-y-3 text-center text-sm text-gray-500 md:text-base">
          <p>
            ここまでご覧いただきありがとうございました！少しでも私のことを知っていただければ幸いです。
          </p>
          <p>
            ご連絡やポートフォリオについてのコメントなどございましたら、<a
              :href="'https://twitter.com/' + settings.twitterAccount"
              target="_blank"
              class="text-cyan-500 hover:text-cyan-600"
              >Twitter</a
            >のDMからお願いいたします。
          </p>
        </div>
        <button></button>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import moment from 'moment'

export default Vue.extend({
  name: 'IndexPage',
  filters: {
    levelToStar: function (value) {
      if (!parseInt(value)) return ''
      var star = ''
      for (let i = 0; i < value; i++) {
        star = star + '★'
      }
      return star
    },
  },
  async asyncData({ $microcms }) {
    const settings = await $microcms.get({
      endpoint: 'settings',
    })
    const carrers = await $microcms.get({
      endpoint: 'carrer',
    })
    const works = await $microcms.get({
      endpoint: 'works',
    })

    const birthday = moment(settings.birthday).format('YYYY年MM月DD日 生まれ')

    return {
      settings,
      birthday,
      carrers,
      exams: require(`@/assets/data/exams.json`),
      skills: require(`@/assets/data/skills.json`),
      works,
    }
  },
})
</script>
