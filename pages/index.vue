<template>
  <div>
    <div id="top" class="min-h-screen flex w-full items-center flex-row-reverse md:flex-row">
      <div class="w-1/2 pr-5 md:w-1/3 md:pr-10"> 
        <p class="text-lg font-semibold tracking-tight text-right">NOKITA's Portfolio</p>
        <ul class="mt-8 mb-5 list-none space-y-5 text-right text-gray-500">
          <li>
            <nuxt-link v-scroll-to="'#about_me'" to class="text-teal-lighter hover:text-cyan-500">
              About me
            </nuxt-link>
          </li>
          <li>
            <nuxt-link v-scroll-to="'#carrer'" to class="text-teal-lighter hover:text-cyan-500">
              Carrer
            </nuxt-link>
          </li>
          <li>
            <nuxt-link v-scroll-to="'#skills'" to class="text-teal-lighter hover:text-cyan-500">
              Skills
            </nuxt-link>
          </li>
          <li>
            <nuxt-link v-scroll-to="'#works'" to class="text-teal-lighter hover:text-cyan-500">
              Works
            </nuxt-link>
          </li>
          <li>
            <nuxt-link v-scroll-to="'#contact_me'" to class="text-teal-lighter hover:text-cyan-500">
              Contact
            </nuxt-link>
          </li>
        </ul>
      </div>
      <div class="w-1/2 md:w-2/3">
        <img class="min-h-screen object-cover" :src="settings.mainImagePC.url+'?w=2000'" alt="top" />
      </div>
    </div>
    <div id="about_me" ref="about_me" class="w-full pb-8 bg-gray-100">
      <Title title="About me" additional="自己紹介"></Title>
      <div class="mx-auto w-5/6 py-8 bg-gray-200 rounded-lg md:w-4/6 md:py-20">
        <div class="flex flex-wrap items-center">
          <div class="w-full md:w-1/2">
            <div>
              <img class="rounded-full w-48 object-cover object-center m-auto" :src="settings.profileImage.url+'?w=300'" alt="step" />
            </div>
          </div>
          <div class="w-full p-5 md:pr-20 md:w-1/2">
            <p class="text-gray-500 text-base font-bold md:text-lg">{{settings.name}}</p>
            <p class="my-3 text-gray-500 text-sm md:my-5 md:text-base">{{birthday}}</p>
            <p class="text-gray-500 text-sm md:text-base">{{settings.selfIntroduction}}</p>
            <div class="flex mx-1 my-5">
              <a :href="'https://github.com/'+settings.githubAccount" target="_blank" >
                <img class="w-6" src="@/assets/image/icon/github.png" />
              </a>
              <a :href="'https://twitter.com/'+settings.twitterAccount" target="_blank" >
                <img class="w-6 my-1 mx-3" src="@/assets/image/icon/twitter.png" />
              </a>
              <a :href="'https://qiita.com/'+settings.qiitarAccount" target="_blank" >
                <img class="w-6" src="@/assets/image/icon/qiita.png" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div id="carrer" class="w-full mr-10">
      <Title title="Carrer" additional="これまでとこれから"></Title>
      <div class="career mx-auto mb-20 md:w-2/3">
        <dl>
          <template v-for="carrer in carrers.contents">
            <dt :key="carrer.period">
              <div class="text-gray-500 text-sm md:text-base">{{carrer.period}}</div>
            </dt>
            <dd :key="carrer.title">
              <CarrerBox :title="carrer.title" :text="carrer.text"></CarrerBox>
            </dd>
          </template>
        </dl>
      </div>
    </div>
    <div id="skills" class="min-h-screen w-full bg-gray-100">
      <Title title="Skills" additional="スキルシート"></Title>
      <div class="mx-10 pb-5 md:w-2/3 md:mx-auto md:pb-20"> 
        <p class="text-base text-gray-500 font-bold md:text-lg">▶ 技術</p>
        <p class="mt-3 text-xs text-gray-500 text-center md:mx-12 md:text-sm">習熟度目安　★：ちょっとさわった　★★：調べながらであれば独力で使える　★★★：プロ</p>
        <div class="mt-5 mb-8 md:mx-12">
          <table class="min-w-full">
            <thead class="border-b">
              <tr>
                <th scope="col" class="text-xs text-gray-500 p-2 text-left md:text-sm md:px-6 md:py-4">
                  カテゴリ
                </th>
                <th scope="col" class="text-xs text-gray-500 p-2 text-left md:text-sm md:px-6 md:py-4">
                  技術名
                </th>
                <th scope="col" class="text-xs text-gray-500 p-2 text-left md:text-sm md:px-6 md:py-4">
                  習熟度
                </th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="skill in skills" :key="skill.name" class="border-b transition duration-300 ease-in-out hover:bg-gray-200">
                <td class="text-xs text-gray-600 font-light p-2 whitespace-nowrap md:text-sm md:px-6 md:py-4">
                  {{skill.category}}
                </td>
                <td class="text-xs text-gray-600 font-light p-2 whitespace-nowrap md:text-sm md:px-6 md:py-4">
                  {{skill.name}}
                </td>
                <td class="text-xs text-gray-600 font-light p-2 whitespace-nowrap md:text-sm md:px-6 md:py-4">
                  {{skill.level | levelToStar}}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <p class="text-base text-gray-500 font-bold md:text-lg">▶ 資格</p>
        <ul class="mt-3 mx-12 list-disc text-sm text-gray-500 space-y-2 md:text-base">
          <li v-for="exam in exams" :key="exam">
            {{exam}}
          </li>
        </ul>
      </div>
    </div>
    <div id="works" class="w-full mr-10">
      <Title title="Works" additional="成果物"></Title>
      <div class="w-full mx-auto pb-5 md:w-2/3 md:pb-20">
        <Accordion :works="works.contents"></Accordion>
      </div>
    </div>
    <div id="contact_me" class="w-full bg-gray-100">
      <Title title="Contact" additional="連絡先"></Title>
      <div class="w-2/3 mx-auto pb-20"> 
        <div class="text-sm text-gray-500 text-center space-y-3 md:text-md">
          <p>ここまでご覧いただきありがとうございました！少しでも私のことを知っていただければ幸いです。</p>
          <p>ご連絡やポートフォリオについてのコメントなどございましたら、<a :href="'https://twitter.com/'+settings.twitterAccount" target="_blank" class="text-cyan-500 hover:text-cyan-600">Twitter</a>のDMからお願いいたします。</p>
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
      var star = ""
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

    const birthday = moment(settings.birthday).format('YYYY年MM月DD日 生まれ');

    return {
      settings,
      birthday,
      carrers,
      exams: require(`@/assets/data/exams.json`),
      skills: require(`@/assets/data/skills.json`),
      works,
    }
  }
})
</script>
