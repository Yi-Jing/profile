<template>
  <div class="flex flex-col items-center justify-center text-white">
    <div class="relative text-sm font-bold after:content-[''] after:block after:w-[80px] after:h-[2px] after:absolute after:-left-[7px] after:bg-[#e4c9fe] after:mt-[2px]">個 人 簡 介</div>
    <div class="w-32 h-32 my-4">
      <img class="shadow-sm rounded-md" :src="info.avatar"/>
    </div>
    <h2 class="font-bold">{{ info.name }}</h2>
    <div class="text-xs mt-2">{{ info.skill }}</div>
  </div>
</template>

<script>

const info = {
  name: '陳 怡 靜',
  avatar: new URL('/images/陳怡靜_1 比 1.jpg', import.meta.url),
  skill: '擅長應用 Vue.js 專注於網頁開發'
}
</script>