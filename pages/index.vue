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
      <img class="w-2/3 object-cover object-center" :src="settings.mainImagePC.url+'?w=2000'" alt="top" />
    </div>
    <div class="min-h-screen w-full bg-gray-100">
      <SubTitle title="About me"></SubTitle>
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
    <div class="w-full mr-10">
      <SubTitle title="Carrer"></SubTitle>
      <div class="career w-2/3 mx-auto mb-20">
        <dl>
          <template v-for="carrer_item in carrer.contents">
            <dt :key="carrer_item.id">
              <div class="text-gray-500">{{carrer_item.period}}</div>
            </dt>
            <dd :key="carrer_item.id">
              <CarrerBox :title="carrer_item.title" :text="carrer_item.text"></CarrerBox>
            </dd>
          </template>
        </dl>
      </div>
    </div>
    <div class="min-h-screen w-full bg-gray-100">
      <SubTitle title="Skills"></SubTitle>
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
              <tr class="border-b transition duration-300 ease-in-out hover:bg-gray-200">
                <td class="text-sm text-gray-600 font-light px-6 py-4 whitespace-nowrap">
                  Frontend
                </td>
                <td class="text-sm text-gray-600 font-light px-6 py-4 whitespace-nowrap">
                  Javascript
                </td>
                <td class="text-sm text-gray-600 font-light px-6 py-4 whitespace-nowrap">
                  ★★
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <p class="text-lg text-gray-500 font-bold">▶ 資格</p>
        <ul class="mt-3 mx-12 list-disc text-gray-500 space-y-2">
          <li v-for="capacity_item in capacity.contents" :key="capacity_item.id">
            {{capacity_item.name}}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import moment from 'moment'
import SubTitle from '~/components/SubTitle'
import CarrerBox from '~/components/CarrerBox'

export default Vue.extend({
  name: 'IndexPage',
  async asyncData({ $microcms }) {
    const settings = await $microcms.get({
      endpoint: 'settings',
    })

    const birthday = moment(settings.birthday).format('YYYY年MM月DD日 生まれ');

    const carrer = await $microcms.get({
      endpoint: 'carrer',
    })

    const capacity = await $microcms.get({
      endpoint: 'capacity',
    })

    return {
      settings,
      birthday,
      carrer,
      capacity,
    }
  }
})
</script>
