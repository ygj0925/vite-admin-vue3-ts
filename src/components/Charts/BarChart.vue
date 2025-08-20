<template>
  <div ref="barChartRef" :data="data" :width="width" :height="height"></div>
</template>

<script setup lang="ts">
import { ref, watch, nextTick, onMounted, onBeforeUnmount } from 'vue'
import * as echarts from 'echarts/core'
import {
  GridComponent,
  GridComponentOption,
  TooltipComponent,
  TooltipComponentOption,
  LegendComponent,
  LegendComponentOption
} from 'echarts/components'
import { BarChart as EBarChart, BarSeriesOption } from 'echarts/charts'
import { CanvasRenderer } from 'echarts/renderers'

echarts.use([GridComponent, TooltipComponent, LegendComponent, EBarChart, CanvasRenderer])

type EChartsOption = echarts.ComposeOption<
  GridComponentOption | TooltipComponentOption | LegendComponentOption | BarSeriesOption
>

defineOptions({
  name: 'BarChart'
})
const props = defineProps({
  data: { type: Array, default: () => [] },
  width: { type: Number, default: 500 },
  height: { type: Number, default: 300 },
  type: { type: String, default: 'bar' }
})

const barChartRef = ref<any>(null)
let chartInstance: echarts.ECharts | null = null
let resizeObserver: any = null
let removeWindowResize: (() => void) | null = null

const init = () => {
  if (!barChartRef.value) return
  if (chartInstance) {
    chartInstance.dispose()
    chartInstance = null
  }
  chartInstance = echarts.init(barChartRef.value)

  const categories = (props.data as any[]).map((d: any) => d.name ?? '')
  const values = (props.data as any[]).map((d: any) => d.value ?? 0)

  const option: EChartsOption = {
    backgroundColor: 'transparent',
    tooltip: { trigger: 'axis' },
    legend: { show: false },
    grid: { left: '3%', right: '4%', bottom: '3%', containLabel: true },
    xAxis: { type: 'category', data: categories },
    yAxis: { type: 'value' },
    series: [
      {
        type: 'bar',
        data: values,
        barMaxWidth: 30
      }
    ]
  }
  chartInstance.setOption(option)
}

const showLoading = () => {
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

onMounted(() => {
  init()
  if ((globalThis as any).ResizeObserver && barChartRef.value) {
    const Rz = (globalThis as any).ResizeObserver
    resizeObserver = new Rz(() => {
      chartInstance?.resize()
    })
    resizeObserver.observe(barChartRef.value)
  } else if (typeof (globalThis as any).addEventListener === 'function') {
    const onWindowResize = () => chartInstance?.resize()
    ;(globalThis as any).addEventListener('resize', onWindowResize)
    removeWindowResize = () => (globalThis as any).removeEventListener('resize', onWindowResize)
  }
})

onBeforeUnmount(() => {
  if (resizeObserver && barChartRef.value) {
    resizeObserver.unobserve(barChartRef.value)
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

watch(
  () => props.data,
  async newVal => {
    await nextTick()
    if (!barChartRef.value) return
    if (!newVal || (Array.isArray(newVal) && newVal.length === 0)) {
      showLoading()
      return
    }
    hideLoading()
    init()
  },
  { deep: true, immediate: true }
)

// 暴露给父组件调用的方法
defineExpose({
  showLoading,
  hideLoading,
  resize: () => chartInstance?.resize(),
  init
})
</script>
