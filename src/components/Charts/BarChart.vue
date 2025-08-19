<template>
  <div class="px-5 py-3">
    <ul ref="legend" class="flex flex-wrap gap-x-4"></ul>
  </div>
  <div class="grow">
    <div ref="charts" :data="data" :width="width" :height="height"></div>
  </div>
</template>

<script setup lang="ts">
defineOptions({
  name: 'BarChart'
})
defineProps({
  data: { type: Array, default: () => [] },
  width: { type: Number, default: 500 },
  height: { type: Number, default: 300 },
  type: { type: String, default: 'bar' }
})
const init = () => {}

const showLoading = () => {
  // loading
}

const hideLoading = () => {
  // loading
}

watch(
  () => props.data,
  (newVal, oldVal) => {
    console.log(newVal, oldVal)
  },
  { deep: true },
  { immediate: true }
)
</script>
