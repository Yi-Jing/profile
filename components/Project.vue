<template>
  <div class="h-[360px] w-[652px] px-6">
    <div class="text-sm text-stone-500 text-left mb-2 w-full">
      <span class="mr-4">專案介紹</span>
    </div>
  
    <div>
      <div
        v-for="(project, index) in projects"
        :key="project.name"
        v-click
        >
        <template v-if="isShow(index)">
          <div class="flex justify-start gap-5 mb-3">
            <div class="w-[40%] h-fit my-4">
              <img class="shadow-md rounded-md object-contain" :src="project.image"/>
            </div>
            <div class="flex flex-col items-start">
              <div class="flex items-center gap-2 mt-6">
                <span class="text-xl font-bold">{{ project.name }}</span>
                <Icon class="mb-[2px]" :path="linkIcon" @click="linkTo(project.link)" />
              </div>
              <span class="mt-2 text-sm text-stone-500">{{ project.content }}</span>
            </div>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router';
import { ref, watch } from 'vue';

const route = useRoute()
const projects = [
  {
    name: '行銷自動化系統',
    image: '/images/project-cover/Linx.png',
    content: '促使百貨公司的行銷人員能自動對顧客發送廣告的系統',
    link: 'https://yi-jing.github.io/linx-file/1'
  },
  {
    name: '高雄智慧走跑',
    image: '/images/project-cover/kaush.png',
    content: '宣傳高雄市政府舉辦走跑活動的一頁式網站',
    link: 'https://kcg-running.tw/'
  },
  {
    name: '新北災訓 E 點通',
    image: '/images/project-cover/disterinfo.png',
    content: '可即時查看新北市周遭附近災情的 SPA 網站',
    link: 'https://e.ntpc.gov.tw/news-info'
  },
  {
    name: '食在營養',
    image: '/images/project-cover/nutrition.png',
    content: '傳達營養師團隊服務的 SSR 網站',
    link: 'https://nutrition.tw/'
  },
  {
    name: 'TSNA 體育新聞團隊',
    image: '/images/project-cover/tsna.png',
    content: '整理體育新聞的 SSR 網站',
    link: 'https://tsna.com/'
  },
  {
    name: '花食間 手作',
    image: '/images/project-cover/Hua Shin Jian.png',
    content: '提供美好餐飲的咖啡廳的 SPA 網站',
    link: 'https://objective-haibt-83b3b9.netlify.app/'
  },
]

const currentClicks = ref('')
watch(
  () => route.query?.clicks,
  (val) => {
    currentClicks.value = val
  },
)

const isShow = (index) => {
  let bool = false

  switch (index) {
    case 0:
    case 1:
      bool = ['1', '2'].includes(currentClicks.value)
      break
    case 2:
    case 3:
      bool = ['3', '4'].includes(currentClicks.value)
      break
    case 4:
    case 5:
      bool = ['5', '6'].includes(currentClicks.value)
      break
    default:
      break
  }

  return bool
}

const linkIcon = ref({
  normal: 'https://cdn-icons-png.flaticon.com/512/7046/7046086.png',
  hover: 'https://cdn-icons-png.flaticon.com/512/282/282100.png'
})
const linkTo = (url) => {
  window.open(url)
}
</script>