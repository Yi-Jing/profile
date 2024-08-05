<template>
  <div class="flex flex-col gap-10 px-6">
    <div
      v-click
      v-for="(skill, index) in skillList"
      :key="skill.name"
      class="min-w-[600px]"
      :class="{ 'absolute': isHidden(index) }"
    >
      <template v-if="isShow(index)">
        <div class="mb-2">
          <span class="text-xl font-bold mr-2">{{ skill.name }}</span>
        </div>
        
        <div class="grid grid grid-cols-6 grid-flow-rows gap-x-4 gap-y-5">
          <div class="flex flex-col items-center justify-between" v-for="(icon, index) in skill.icons" :key="`${skill.name}-${index}`">
            <div class="flex items-center justify-center w-20 h-12 overflow-hidden">
              <img class="w-full h-full rounded-md object-contain" :src="icon" />
            </div>
            <span class="pt-1 text-xs text-stone-500">{{ skill.tools[index] }}</span>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router';
import { ref, watch } from 'vue';

const skillList = [
  {
    name: '前端開發',
    level: '精通',
    tools: [
      'Vue.js',
      'Vite',
      'NuxtJS',
      'Pinia',
      'Pug',
      'React.js',
      'NextJS',
      'Tailwind CSS',
      'Scss',
      'JavaScript',
      'TypeScript',
      'Axios',
      'npm',
      'yarn'
    ],
    icons: [
      'https://www.svgrepo.com/show/354528/vue.svg',
      'https://www.svgrepo.com/show/354521/vitejs.svg',
      'https://www.svgrepo.com/show/354131/nuxt-icon.svg',
      'https://upload.wikimedia.org/wikipedia/commons/1/1c/Pinialogo.svg',
      'https://www.svgrepo.com/show/374012/pug.svg',
      'https://static-00.iconduck.com/assets.00/react-icon-2048x2048-o8k3ymqa.png',
      'https://www.svgrepo.com/show/354113/nextjs-icon.svg',
      'https://www.svgrepo.com/show/333609/tailwind-css.svg',
      'https://www.svgrepo.com/show/374068/scss.svg',
      'https://www.svgrepo.com/show/303206/javascript-logo.svg',
      'https://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Typescript_logo_2020.svg/2048px-Typescript_logo_2020.svg.png',
      'https://cdn.worldvectorlogo.com/logos/axios.svg',
      'https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Npm-logo.svg/2560px-Npm-logo.svg.png',
      'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSaRWKEVUYoBgUOjgsIrQP19cFWeOfTtpllEA4DG0UTGKBKY5trUpvNi9_Mvk96DifYgMY&usqp=CAU'
    ]
  },
  {
    name: '後端開發',
    level: '初學',
    tools: ['PostgreSQL'],
    icons: ['https://static-00.iconduck.com/assets.00/postgresql-icon-1987x2048-v2fkmdaw.png']
  },
  {
    name: '版本控制',
    level: '精通',
    tools: ['Git', 'GitHub', 'GitLab', 'CLI', 'Sourcetree'],
    icons: [
      'https://avatars.githubusercontent.com/u/18133?s=280&v=4',
      'https://upload.wikimedia.org/wikipedia/commons/thumb/c/c2/GitHub_Invertocat_Logo.svg/180px-GitHub_Invertocat_Logo.svg.png',
      'https://www.cloudservices.store/site/wp-content/uploads/2020/10/logo-extra-whitespace.png',
      'https://www.freeiconspng.com/thumbs/command-line-icon/command-line-icon-1.png',
      'https://static-00.iconduck.com/assets.00/sourcetree-icon-407x512-cnpohnjl.png'
    ]
  },
  {
    name: '介面開發',
    level: '初學',
    tools: ['Android Studio'],
    icons: ['https://static-00.iconduck.com/assets.00/android-studio-icon-486x512-zp9um7zl.png']
  },
]

const route = useRoute()
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
      bool = currentClicks.value === '3'
      break
    case 3:
      bool = currentClicks.value === '4'
      break
    default:
      break
  }

  return bool
}

const isHidden = (index) => {
  let bool = false

  switch (currentClicks.value) {
    case '1':
    case '2':
      bool = [2, 3].includes(index)
      break
    case '3':
      bool = [0, 1, 3].includes(index)
      break
    case '4':
      bool = [0, 1, 2].includes(index)
      break
  }

  return bool
}
</script>