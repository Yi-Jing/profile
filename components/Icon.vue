<template>
  <div
    class="w-5 h-5 cursor-pointer"
    @mouseover="handleLinkIconColor('hover')"
    @mouseleave="handleLinkIconColor('normal')"
  >
    <img 
      class="w-full h-full object-cover"
      :src="linkIcon"
    />
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';

const props = defineProps({
  path: {
    type: Object,
    default: () => {
      return {
        normal: '',
        hover: ''
      }
    },
  }
})

const linkIcon = ref(props.path.normal)
const handleLinkIconColor = (action) => {
  return linkIcon.value = action === 'hover' ? props.path.hover : props.path.normal
}
</script>