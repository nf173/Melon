<template>
  <!-- 
    aria-hidden=“true” ：
    配合无障碍阅读 语义化隐藏
    避免屏幕识读设备抓取
  -->
  <svg
  :class="svgClass" 
  :style="size?`width:${size}px;height:${size}px;`:''" aria-hidden="true">
    <use :xlink:href="iconName" />
  </svg>
</template>

<script setup lang="ts">
import { computed } from "vue"

const props = defineProps({
  name: {
    type: String,
    required: true
  },
  color: {
    type: String,
    default: ''
  },
  size: {
    type:[Number,String],
    default: 14
  }
})

const iconName = computed(() => `#${props.name}`)
const svgClass = computed(() => {
  if (props.name) {
     return `svg-icon ${props.name}`
  }
  return "svg-icon"
})
</script>

<style scoped>
.svg-icon {
  fill: currentColor;
  vertical-align: middle;
  outline: none;
}
</style>