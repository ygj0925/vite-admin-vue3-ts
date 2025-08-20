<template>
  <div class="grid grid-cols-12 gap-6">
    <div
      class="flex flex-col col-span-full sm:col-span-6 xl:col-span-4 bg-white dark:bg-gray-800 shadow-xs rounded-xl"
    >
      <div class="px-5 pt-5">
        <header class="flex justify-between items-start mb-2">
          <h2 class="text-lg font-semibold text-gray-800 dark:text-gray-100">Acme Plus</h2>
          <EditMenu align="right" class="relative inline-flex">
            <li>
              <a
                class="font-medium text-sm text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-gray-200 flex py-1 px-3"
                href="#0"
                >Option 1</a
              >
            </li>
            <li>
              <a
                class="font-medium text-sm text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-gray-200 flex py-1 px-3"
                href="#0"
                >Option 2</a
              >
            </li>
            <li>
              <a
                class="font-medium text-sm text-red-500 hover:text-red-600 flex py-1 px-3"
                href="#0"
                >Remove</a
              >
            </li>
          </EditMenu>
        </header>
        <div class="text-xs font-semibold text-gray-400 dark:text-gray-500 uppercase mb-1">
          Sales
        </div>
        <div class="flex items-start">
          <div class="text-3xl font-bold text-gray-800 dark:text-gray-100 mr-2">$24,780</div>
          <div class="text-sm font-medium text-green-700 px-1.5 bg-green-500/20 rounded-full">
            +49%
          </div>
        </div>
      </div>
      <div class="px-5 pb-5 max-sm:max-h-[198px] xl:max-h-[198px]">
        <LineChart ref="lineChartRef" :data="lineData" width="100" height="178" />
      </div>
    </div>
    <div
      class="flex flex-col col-span-full sm:col-span-6 xl:col-span-4 bg-white dark:bg-gray-800 shadow-xs rounded-xl"
    >
      <div class="px-5 pt-5">
        <header class="flex justify-between items-start mb-2">
          <h2 class="text-lg font-semibold text-gray-800 dark:text-gray-100">Acme Plus</h2>
          <EditMenu align="right" class="relative inline-flex">
            <li>
              <a
                class="font-medium text-sm text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-gray-200 flex py-1 px-3"
                href="#0"
                >Option 1</a
              >
            </li>
            <li>
              <a
                class="font-medium text-sm text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-gray-200 flex py-1 px-3"
                href="#0"
                >Option 2</a
              >
            </li>
            <li>
              <a
                class="font-medium text-sm text-red-500 hover:text-red-600 flex py-1 px-3"
                href="#0"
                >Remove</a
              >
            </li>
          </EditMenu>
        </header>
        <div class="text-xs font-semibold text-gray-400 dark:text-gray-500 uppercase mb-1">
          Sales
        </div>
        <div class="flex items-start">
          <div class="text-3xl font-bold text-gray-800 dark:text-gray-100 mr-2">$24,780</div>
          <div class="text-sm font-medium text-green-700 px-1.5 bg-green-500/20 rounded-full">
            +49%
          </div>
        </div>
      </div>
      <div class="px-5 pb-5 max-sm:max-h-[128px] xl:max-h-[128px]">
        <!-- <BarChart ref="barChartRef" :data="barData" width="389" height="128" /> -->
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import * as echarts from 'echarts/core'
import LineChart from '@/components/Charts/LineChart.vue'
import BarChart from '@/components/Charts/BarChart.vue'
import EditMenu from './compontents/DropdownEditMenu.vue'
defineOptions({ name: 'MarketingManangeReport' })

type LineChartExposed = {
  showLoading: () => void
  hideLoading: () => void
  resize: () => void
  initChart: () => void
}

type BarChartExposed = {
  showLoading: () => void
  hideLoading: () => void
  resize: () => void
  initChart: () => void
}

const lineChartRef = ref<LineChartExposed | null>(null)
const barChartRef = ref<BarChartExposed | null>(null)
const lineData = ref<any>(null)
const barData = ref<any>(null)
const chartData = ref({
  labels: [
    '12-01-2022',
    '01-01-2023',
    '02-01-2023',
    '03-01-2023',
    '04-01-2023',
    '05-01-2023',
    '06-01-2023',
    '07-01-2023',
    '08-01-2023',
    '09-01-2023',
    '10-01-2023',
    '11-01-2023',
    '12-01-2023',
    '01-01-2024',
    '02-01-2024',
    '03-01-2024',
    '04-01-2024',
    '05-01-2024',
    '06-01-2024',
    '07-01-2024',
    '08-01-2024',
    '09-01-2024',
    '10-01-2024',
    '11-01-2024',
    '12-01-2024',
    '01-01-2025'
  ],
  datasets: [
    // Indigo line
    {
      data: [
        732, 610, 610, 504, 504, 504, 349, 349, 504, 342, 504, 610, 391, 192, 154, 273, 191, 191,
        126, 263, 349, 252, 423, 622, 470, 532
      ],
      fill: true,
      borderWidth: 2,
      pointRadius: 0,
      pointHoverRadius: 3,
      pointBorderWidth: 0,
      pointHoverBorderWidth: 0,
      clip: 20,
      tension: 0.2
    },
    // Gray line
    {
      data: [
        532, 532, 532, 404, 404, 314, 314, 314, 314, 314, 234, 314, 234, 234, 314, 314, 314, 388,
        314, 202, 202, 202, 202, 314, 720, 642
      ],
      borderWidth: 2,
      pointRadius: 0,
      pointHoverRadius: 3,
      pointBorderWidth: 0,
      pointHoverBorderWidth: 0,
      clip: 20,
      tension: 0.2
    }
  ]
})

onMounted( async () => {
  // 显示 loading
  await nextTick()
  lineChartRef.value?.showLoading()

  // 异步获取数据后
  setTimeout(() => {
    lineData.value = {
      backgroundColor: 'transparent',
      tooltip: {
        show: true,
        trigger: 'axis'
      },
      xAxis: {
        show: false,
        type: 'category',
        boundaryGap: false,
        data: [
          '12-01-2022',
          '01-01-2023',
          '02-01-2023',
          '03-01-2023',
          '04-01-2023',
          '05-01-2023',
          '06-01-2023',
          '07-01-2023',
          '08-01-2023',
          '09-01-2023',
          '10-01-2023',
          '11-01-2023',
          '12-01-2023',
          '01-01-2024',
          '02-01-2024',
          '03-01-2024',
          '04-01-2024',
          '05-01-2024',
          '06-01-2024',
          '07-01-2024',
          '08-01-2024',
          '09-01-2024',
          '10-01-2024',
          '11-01-2024',
          '12-01-2024',
          '01-01-2025'
        ]
      },
      grid: {
        width: '100%',
        height: '100%',
        top: '0%',
        left: '0%',
        right: '0%',
        bottom: '0%'
        // containLabel: true
      },
      yAxis: {
        show: false,
        type: 'value'
      },
      series: [
        {
          name: '今年',
          type: 'line',
          showAllSymbol: true,
          symbolSize: 1,
          smooth: true,
          lineStyle: {
            normal: {
              width: 2,
              color: '#8470ff' // 线条颜色
            },
            borderColor: 'rgba(0,0,0,.4)'
          },
          tooltip: {
            show: true
          },
          areaStyle: {
            normal: {
              color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                {
                  offset: 0,
                  color: '#8470ff'
                },
                {
                  offset: 0.8,
                  color: 'rgba(255, 255, 255, 0)'
                }
              ])
            }
          },
          data: [
            732, 610, 610, 504, 504, 504, 349, 349, 504, 342, 504, 610, 391, 192, 154, 273, 191,
            191, 126, 263, 349, 252, 423, 622, 470, 532
          ]
        },
        {
          name: '去年',
          type: 'line',
          showAllSymbol: false,
          symbolSize: 0,
          smooth: true,
          emphasis: {
            focus: 'none',
            lineStyle: { color: '#dee0e3', width: 2 },
            itemStyle: { color: '#dee0e3' }
          },
          lineStyle: {
            normal: {
              width: 2,
              color: '#dee0e3' // 线条颜色
            },
            borderColor: 'rgba(0,0,0,.4)'
          },
          itemStyle: {
            color: 'rgba(25,163,223,1)',
            borderColor: '#646ace',
            borderWidth: 2
          },
          tooltip: {
            show: true
          },
          data: [
            532, 532, 532, 404, 404, 314, 314, 314, 314, 314, 234, 314, 234, 234, 314, 314, 314,
            388, 314, 202, 202, 202, 202, 314, 720, 642
          ]
        }
      ]
    }
    // lineChartRef.value?.hideLoading()
  }, 1000)
})
</script>
