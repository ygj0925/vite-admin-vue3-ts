<template>
  <div
    ref="chartsRef"
    :style="containerStyle"
  ></div>
</template>
<!-- 

:style="{ width: containerStyle.width, height: containerStyle.height }" 
-->

<script setup lang="ts">
import { ref, watch, nextTick, onMounted, onBeforeUnmount } from 'vue'
import * as echarts from 'echarts/core'
import { GridComponent, GridComponentOption } from 'echarts/components'
import { LineChart, LineSeriesOption } from 'echarts/charts'
import { UniversalTransition } from 'echarts/features'
import { CanvasRenderer } from 'echarts/renderers'

echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition])

type EChartsOption = echarts.ComposeOption<GridComponentOption | LineSeriesOption>

defineOptions({
  name: 'LineChart'
})
const props = defineProps({
  data: { type: Object, default: () => {} },
  width: { type: [Number, String], default: 500 },
  height: { type: [Number, String], default: 300 },
  type: { type: String, default: 'bar' }
})

const chartsRef = ref<any>(null)
let chartInstance: echarts.ECharts | null = null
let resizeObserver: any = null
let removeWindowResize: (() => void) | null = null

const showLoading = () => {
  console.log(chartInstance, 'chartInstance')
  if (!chartInstance) return
  chartInstance.showLoading('default', {
    text: '加载中…',
    color: '#1890ff',
    maskColor: 'rgba(0,0,0,0.05)'
  })
}

const hideLoading = () => {
  if (!chartInstance) return
  chartInstance.hideLoading()
}
const initChart = () => {
  if (!chartsRef.value) return

  if (chartInstance) {
    chartInstance.dispose()
    chartInstance = null
  }

  chartInstance = echarts.init(chartsRef.value)
  const options: EChartsOption = props.data
  options && chartInstance.setOption(options)
}

onMounted(() => {
  initChart()
  if ((globalThis as any).ResizeObserver && chartsRef.value) {
    const Rz = (globalThis as any).ResizeObserver
    resizeObserver = new Rz(() => {
      chartInstance?.resize()
    })
    resizeObserver.observe(chartsRef.value)
  } else if (typeof (globalThis as any).addEventListener === 'function') {
    const onWindowResize = () => chartInstance?.resize()
    ;(globalThis as any).addEventListener('resize', onWindowResize)
    removeWindowResize = () => (globalThis as any).removeEventListener('resize', onWindowResize)
  }
})

onBeforeUnmount(() => {
  if (resizeObserver && chartsRef.value) {
    resizeObserver.unobserve(chartsRef.value)
    resizeObserver.disconnect()
    resizeObserver = null
  }
  if (removeWindowResize) {
    removeWindowResize()
    removeWindowResize = null
  }
  if (chartInstance) {
    chartInstance.dispose()
    chartInstance = null
  }
})

const containerStyle = computed(() => ({
  width: typeof props.width === 'number' ? props.width + 'px' : props.width,
  height: typeof props.height === 'number' ? props.height + 'px' : props.height
}))

watch([() => props.width, () => props.height], () => nextTick(() => chartInstance?.resize()))

watch(
  () => props.data,
  async () => {
    await nextTick()

    if (!chartsRef.value) return
    if (!props.data) {
      showLoading()
      return
    }
    hideLoading()
    initChart()
  },
  { deep: true, immediate: true }
)

// 暴露给父组件调用的方法
defineExpose({
  showLoading,
  hideLoading,
  resize: () => chartInstance?.resize(),
  initChart
})
</script>
