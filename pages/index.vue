<template>
  <div>
    <div id="top" class="min-h-screen flex flex-wrap w-full items-center">
      <div class="w-1/3">
        <div class="mr-10">
          <p class="text-lg font-semibold tracking-tight text-right">KITANO's Portfolio</p>
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
                Contact me
              </nuxt-link>
            </li>
          </ul>
        </div>
      </div>
      <img class="w-2/3 min-h-screen object-cover" :src="settings.mainImagePC.url+'?w=2000'" alt="top" />
    </div>
    <div id="about_me" ref="about_me" class="min-h-screen w-full bg-gray-100">
      <Title title="About me" additional="自己紹介"></Title>
      <div class="mx-auto w-4/6 bg-profile rounded-lg py-20">
        <div class="flex flex-wrap items-center">
          <div class="w-1/2">
            <div>
              <img class="rounded-full w-48 object-cover object-center m-auto" :src="settings.profileImage.url+'?w=300'" alt="step" />
            </div>
          </div>
          <div class="w-1/2 pr-20">
            <p class="text-white text-lg font-bold">{{settings.name}}</p>
            <p class="text-white my-5">{{birthday}}</p>
            <p class="text-white">{{settings.selfIntroduction}}</p>
          </div>
        </div>
      </div>
    </div>
    <div id="carrer" class="w-full mr-10">
      <Title title="Carrer" additional="これまでとこれから"></Title>
      <div class="career w-2/3 mx-auto mb-20">
        <dl>
          <template v-for="carrer in carrers">
            <dt :key="carrer.period">
              <div class="text-gray-500">{{carrer.period}}</div>
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
      <div class="w-2/3 mx-auto pb-20"> 
        <p class="text-lg text-gray-500 font-bold">▶ 技術</p>
        <p class="mt-3 mx-12 text-sm text-gray-500 text-center">習熟度目安　★：ちょっとさわった 　★★：調べながらであれば独力で使える　★★★：プロ</p>
        <div class="mt-5 mb-8 mx-12">
          <table class="min-w-full">
            <thead class="border-b">
              <tr>
                <th scope="col" class="text-sm text-gray-500 px-6 py-4 text-left">
                  カテゴリ
                </th>
                <th scope="col" class="text-sm text-gray-500 px-6 py-4 text-left">
                  技術名
                </th>
                <th scope="col" class="text-sm text-gray-500 px-6 py-4 text-left">
                  習熟度
                </th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="skill in skills" :key="skill.name" class="border-b transition duration-300 ease-in-out hover:bg-gray-200">
                <td class="text-sm text-gray-600 font-light px-6 py-4 whitespace-nowrap">
                  {{skill.category}}
                </td>
                <td class="text-sm text-gray-600 font-light px-6 py-4 whitespace-nowrap">
                  {{skill.name}}
                </td>
                <td class="text-sm text-gray-600 font-light px-6 py-4 whitespace-nowrap">
                  {{skill.level | levelToStar}}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <p class="text-lg text-gray-500 font-bold">▶ 資格</p>
        <ul class="mt-3 mx-12 list-disc text-gray-500 space-y-2">
          <li v-for="exam in exams" :key="exam">
            {{exam}}
          </li>
        </ul>
      </div>
    </div>
    <div id="works" class="w-full mr-10">
      <Title title="Works" additional="成果物"></Title>
      <div class="w-2/3 mx-auto pb-20">
        <Accordion :works="works.contents"></Accordion>
      </div>
    </div>
    <div id="contact_me" class="w-full bg-gray-100">
      <Title title="Contact me" additional="連絡先"></Title>
      <div class="w-2/3 mx-auto pb-20"> 
        <div class="text-gray-500 text-center space-y-3">
          <p>ここまでご覧いただきありがとうございました！少しでも私のことを知っていただければ幸いです。</p>
          <p>ご連絡やポートフォリオについてのコメントなどございましたら、<a href="https://twitter.com/maakitakita" target="_blank" class="text-cyan-500 hover:text-cyan-600">Twitter</a>のDMからお願いいたします。</p>
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
    const works = await $microcms.get({
      endpoint: 'works',
    })

    const birthday = moment(settings.birthday).format('YYYY年MM月DD日 生まれ');

    return {
      settings,
      birthday,
      carrers: require(`@/assets/data/carrers.json`),
      exams: require(`@/assets/data/exams.json`),
      skills: require(`@/assets/data/skills.json`),
      works,
    }
  }
})
</script>
