<template>
  <div>
    <div
      v-click
      v-for="(skill, index) in skillList"
      :key="skill.name"
      class="min-w-[600px]"
    >
      <div class="mb-10" v-if="isShow(index)">
        <div class="mb-2">
          <span class="text-xl font-bold mr-2">{{ skill.name }}</span>
        </div>

        <div class="grid grid grid-cols-6 grid-flow-rows gap-x-4 gap-y-5">
          <div
            class="flex flex-col items-center justify-between"
            v-for="(icon, index) in skill.icons"
            :key="`${skill.name}-${index}`"
          >
            <div
              class="flex items-center justify-center w-20 h-12 overflow-hidden"
            >
              <img
                class="w-full h-full rounded-md object-contain"
                :src="icon"
              />
            </div>
            <span class="pt-1 text-xs text-stone-500">{{
              skill.tools[index]
            }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import { ref, watch } from 'vue'

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
      'yarn',
      // 'Angular',
    ],
    icons: [
      new URL('/images/skills/vue.svg', import.meta.url),
      new URL('/images/skills/vite.svg', import.meta.url),
      new URL('/images/skills/nuxt.svg', import.meta.url),
      new URL('/images/skills/pinia.svg', import.meta.url),
      new URL('/images/skills/pug.svg', import.meta.url),
      new URL('/images/skills/react.png', import.meta.url),
      new URL('/images/skills/next.svg', import.meta.url),
      new URL('/images/skills/tailwind.svg', import.meta.url),
      new URL('/images/skills/scss.svg', import.meta.url),
      new URL('/images/skills/javascript.svg', import.meta.url),
      new URL('/images/skills/typescript.png', import.meta.url),
      new URL('/images/skills/axios.svg', import.meta.url),
      new URL('/images/skills/npm.png', import.meta.url),
      new URL('/images/skills/yarn.png', import.meta.url),
      // new URL('/images/skills/angular.png', import.meta.url),
    ],
  },
  {
    name: '後端開發',
    level: '初學',
    tools: ['Java', 'Spring', 'Spring Boot', 'PostgreSQL'],
    icons: [
      new URL('/images/skills/java.png', import.meta.url),
      new URL('/images/skills/spring.svg', import.meta.url),
      new URL('/images/skills/spring-boot.webp', import.meta.url),
      new URL('/images/skills/postgresql.png', import.meta.url),
    ],
  },
  {
    name: '版本控制',
    level: '精通',
    tools: ['Git', 'GitHub', 'GitLab', 'CLI', 'Sourcetree'],
    icons: [
      new URL('/images/skills/git.png', import.meta.url),
      new URL('/images/skills/github.png', import.meta.url),
      new URL('/images/skills/gitlab.png', import.meta.url),
      new URL('/images/skills/CLI.png', import.meta.url),
      new URL('/images/skills/sourcetree.png', import.meta.url),
    ],
  },
  {
    name: '介面開發',
    level: '初學',
    tools: ['Android Studio'],
    icons: [new URL('/images/skills/android-studio.png', import.meta.url)],
  },
]

const route = useRoute()
const currentClicks = ref('')
watch(
  () => route.query?.clicks,
  (val) => {
    currentClicks.value = val
  }
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
</script>
