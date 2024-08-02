<template>
  <div class="flex flex-col items-center justify-center text-white">
    <div class="relative text-sm font-bold after:content-[''] after:block after:w-[80px] after:h-[2px] after:absolute after:-left-[7px] after:bg-[#e4c9fe] after:mt-[2px]">個 人 簡 介</div>
    <div class="w-26 h-26 my-4">
      <img class="shadow-sm rounded-md" :src="info.avatar"/>
    </div>
    <h2 class="font-bold">{{ info.name }}</h2>
    <div class="text-xs mt-2">{{ info.age }}</div>
    <div class="text-xs">{{ info.school }}</div>
  </div>
</template>

<script>

const info = {
  name: '陳 怡 靜',
  age: '28歲',
  avatar: '/images/陳怡靜_1 比 1.jpg',
  school: '私立長榮大學 資訊管理學系'
}
</script>