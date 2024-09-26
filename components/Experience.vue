<template>
  <div class="px-6">
    <div v-click="1" class="text-sm text-stone-500 mb-4 ml-6">
      <span class="mr-4">工作經驗</span>
    </div>

    <div class="flex flex-col gap-10 w-[600px]">
      <div v-click v-for="experience in experienceList" :key="experience.key" class="experience">
        <div class="dot flex items-center gap-4 font-bold text-2xl">{{ experience.role }}</div>
        <div class="line relative pl-6">
          <div class="flex items-center gap-3 pt-1 pb-3">
            <div>{{ experience.company }}</div>
            <div>{{ experience.timeInOffice }}</div>
          </div>
          <div class="text-sm text-stone-500">
            <!-- <div class="whitespace-pre-line">{{ experience.content }}</div> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const experienceList = [
  {
    key: 'datarget',
    role: '前端工程師',
    company: '騰創數析股份有限公司',
    timeInOffice: '2023/6~仍在職',
    content: '負責網頁前台（含RWD）的開發，針對企劃產出的規格書，決策該使用何種 Web 框架和需要的機制、套件，並規劃系統架構、路由，根據 UI/UX 的設計稿進行開發並與後端配合處理資料的串接。',
  },
  // {
  //   key: 'redfoxes',
  //   role: '前端工程組長',
  //   company: '赤狐有限公司',
  //   timeInOffice: '2022/12~仍在職',
  //   content: '主導該公司網頁相關業務規劃，訂定開發流程與規範，為每項專案規劃規範技術棧，並與後端協調 API 串接的資料結構、與 UI/UX 協調最佳的使用者體驗，替客戶設計出一款真正適合他們的網頁。',
  // },
  {
    key: 'miracle',
    role: '前端工程師',
    company: '奇迹科技股份有限公司',
    timeInOffice: '2021/4~2023/3',
    content: '負責網頁前台（含RWD）的開發，針對企劃產出的規格書，完成頁面、套版、特效、互動設計等需求，根據 UI/UX 的設計稿，進行頁面切版，並與後端配合處理資料的串接。',
  }
]
</script>

<style>
.line::before {
  @apply absolute -top-3 left-[3px] block content-[''] w-[2px] bg-[#c6ace0];

  height: calc(100% + 65px);
}


.experience:last-child .line::before {
  height: calc(100% + 26px);
}

.dot::before {
  @apply block content-[''] w-2 h-2 rounded bg-[#c6ace0];
}
</style>