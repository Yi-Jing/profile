
<div class="flex">
  <div class="left-area absolute top-0 left-0 bg-[#c6ace0] w-1/3 h-full flex items-center justify-center">
    <div class="flex flex-col items-center justify-center text-white">
      <div class="relative text-sm font-bold after:content-[''] after:block after:w-[80px] after:h-[2px] after:absolute after:-left-[7px] after:bg-[#e4c9fe] after:mt-[2px]">專 業 技 能</div>
      <div class="w-28 h-full">
        <img src="https://cdn-icons-png.flaticon.com/512/3439/3439971.png"/>
      </div>
        <h2 class="text-lg font-bold">{{ title }}</h2>
    </div>
  </div>

  <div class="right-area absolute top-0 right-0 w-2/3 h-full flex flex-col justify-center items-center">
      <Skill />
  </div>
</div>

<script setup>
import { useRoute } from 'vue-router';
import { ref, watch } from 'vue';

const route = useRoute()
const title = ref('網 頁 開 發')
watch(
  () => route.query?.clicks,
  (val) => {
    title.value = val === '4' ? 'App 開發' : '網 頁 開 發'
  },
)
</script>