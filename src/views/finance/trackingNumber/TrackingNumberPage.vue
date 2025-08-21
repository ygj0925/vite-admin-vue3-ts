<template>
  <div class="grid grid-cols-12 gap-6">
    <div
      class="flex flex-col col-span-full sm:col-span-6 xl:col-span-3 bg-white dark:bg-gray-800 shadow-xs rounded-xl"
    >
    <div class="grid md:grid-cols-2 gap-8">
          <div class="p-8 md:p-12 flex flex-col justify-center">
            <span class="text-white/80 text-sm font-medium mb-4 inline-block">核心总览</span>
            <h3 class="text-[clamp(1.5rem,3vw,2.2rem)] font-bold text-white mb-6">
              主要内容概览与分析
            </h3>
            <p class="text-white/90 mb-8 text-lg">
              这里展示主要内容和核心数据，提供整体概览和关键信息。通过总区域可以快速了解整体情况和重要指标。
            </p>
            <div class="grid grid-cols-3 gap-4 mb-8">
              <div class="bg-white/10 backdrop-blur-sm rounded-xl p-4 text-center">
                <div class="text-white text-2xl font-bold mb-1">89%</div>
                <div class="text-white/80 text-sm">完成率</div>
              </div>
              <div class="bg-white/10 backdrop-blur-sm rounded-xl p-4 text-center">
                <div class="text-white text-2xl font-bold mb-1">1,248</div>
                <div class="text-white/80 text-sm">总量</div>
              </div>
              <div class="bg-white/10 backdrop-blur-sm rounded-xl p-4 text-center">
                <div class="text-white text-2xl font-bold mb-1">+12.5%</div>
                <div class="text-white/80 text-sm">增长率</div>
              </div>
            </div>
            <button class="self-start px-6 py-3 bg-white text-primary rounded-full font-medium hover:bg-gray-100 transition-colors shadow-lg">
              查看详情 <i class="fa fa-arrow-right ml-2"></i>
            </button>
          </div>
          <div class="bg-white/5 backdrop-blur-sm p-8 flex items-center justify-center">
            <div class="w-full h-full max-w-md">
              <!-- 模拟图表 -->
              <div class="bg-white/10 backdrop-blur-md rounded-xl p-6 h-full flex flex-col justify-center">
                <div class="flex justify-between items-center mb-6">
                  <h4 class="text-white font-medium">数据趋势</h4>
                  <div class="text-white/80 text-sm">近30天</div>
                </div>
                <div class="space-y-6">
                  <div>
                    <div class="flex justify-between text-white/80 text-sm mb-1">
                      <span>类别A</span>
                      <span>85%</span>
                    </div>
                    <div class="h-3 bg-white/20 rounded-full overflow-hidden">
                      <div class="h-full bg-white rounded-full" style="width: 85%"></div>
                    </div>
                  </div>
                  <div>
                    <div class="flex justify-between text-white/80 text-sm mb-1">
                      <span>类别B</span>
                      <span>62%</span>
                    </div>
                    <div class="h-3 bg-white/20 rounded-full overflow-hidden">
                      <div class="bg-white rounded-full" style="width: 62%"></div>
                    </div>
                  </div>
                  <div>
                    <div class="flex justify-between text-white/80 text-sm mb-1">
                      <span>类别C</span>
                      <span>45%</span>
                    </div>
                    <div class="h-3 bg-white/20 rounded-full overflow-hidden">
                      <div class="h-full bg-white rounded-full" style="width: 45%"></div>
                    </div>
                  </div>
                  <div>
                    <div class="flex justify-between text-white/80 text-sm mb-1">
                      <span>类别D</span>
                      <span>92%</span>
                    </div>
                    <div class="h-3 bg-white/20 rounded-full overflow-hidden">
                      <div class="h-full bg-white rounded-full" style="width: 92%"></div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
    </div>
    <div
      class="flex flex-col col-span-full sm:col-span-6 xl:col-span-3 bg-white dark:bg-gray-800 shadow-xs rounded-xl"
    >
      <div class="px-5 pt-5">
        <header class="flex justify-between items-start mb-2">
          <h2 class="text-lg font-semibold text-gray-800 dark:text-gray-100">TBU</h2>
          <EditMenu align="right" class="relative inline-flex">
            <li>
              <a
                class="font-medium text-sm text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-gray-200 flex py-1 px-3"
                href="#0"
                >6个月</a
              >
            </li>
            <li>
              <a
                class="font-medium text-sm text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-gray-200 flex py-1 px-3"
                href="#0"
                >一年</a
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
          学术接受度
        </div>
        <div class="flex items-start">
          <div class="text-3xl font-bold text-gray-800 dark:text-gray-100 mr-2">$24,780</div>
          <div class="text-sm font-medium text-green-700 px-1.5 bg-green-500/20 rounded-full">
            +49%
          </div>
        </div>
      </div>
      <div class="px-5 pb-5 max-sm:max-h-[158px] xl:max-h-[158px]">
        <LineChart ref="lineTbuChartRef" :data="lineTbuData" width="100%" height="158px" />
      </div>
    </div>
    <div
      class="flex flex-col col-span-full sm:col-span-6 xl:col-span-3 bg-white dark:bg-gray-800 shadow-xs rounded-xl"
    >
      <div class="px-5 pt-5">
        <header class="flex justify-between items-start mb-2">
          <h2 class="text-lg font-semibold text-gray-800 dark:text-gray-100">EBU</h2>
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
          学术接受度
        </div>
        <div class="flex items-start">
          <div class="text-3xl font-bold text-gray-800 dark:text-gray-100 mr-2">$24,780</div>
          <div class="text-sm font-medium text-green-700 px-1.5 bg-green-500/20 rounded-full">
            +49%
          </div>
        </div>
      </div>
      <div class="px-5 pb-5 max-sm:max-h-[158px] xl:max-h-[158px]">
        <LineChart ref="lineEbuChartRef" :data="lineEbuData" width="100%" height="158px" />
      </div>
    </div>
    <div
      class="flex flex-col col-span-full sm:col-span-6 xl:col-span-3 bg-white dark:bg-gray-800 shadow-xs rounded-xl"
    >
      <div class="px-5 pt-5">
        <header class="flex justify-between items-start mb-2">
          <h2 class="text-lg font-semibold text-gray-800 dark:text-gray-100">GBU</h2>
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
          学术接受度
        </div>
        <div class="flex items-start">
          <div class="text-3xl font-bold text-gray-800 dark:text-gray-100 mr-2">$24,780</div>
          <div class="text-sm font-medium text-green-700 px-1.5 bg-green-500/20 rounded-full">
            +49%
          </div>
        </div>
      </div>
      <div class="px-5 pb-5 max-sm:max-h-[158px] xl:max-h-[158px]">
        <LineChart ref="lineGbuChartRef" :data="lineGbuData" width="100%" height="158px" />
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

const lineTbuChartRef = ref<LineChartExposed | null>(null)
const lineEbuChartRef = ref<LineChartExposed | null>(null)
const lineGbuChartRef = ref<LineChartExposed | null>(null)
const lineTbuData = ref<any>(null)
const lineEbuData = ref<any>(null)
const lineGbuData = ref<any>(null)
  
const barChartRef = ref<BarChartExposed | null>(null)
const barData = ref<any>(null)

onMounted(async () => {
  // 显示 loading
  await nextTick()
  lineTbuChartRef.value?.showLoading()
  lineEbuChartRef.value?.showLoading()
  lineGbuChartRef.value?.showLoading()

  // 异步获取数据后
  setTimeout(() => {
    lineTbuData.value = {
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
          symbolSize: 0,
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
                  color: 'rgba(153, 132, 255, .4)'
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
            color: '#dee0e3',
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
    lineEbuData.value = {
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
          symbolSize: 0,
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
                  color: 'rgba(153, 132, 255, .4)'
                },
                {
                  offset: 0.8,
                  color: 'rgba(255, 255, 255, 0)'
                }
              ])
            }
          },
          data: [
            622, 622, 426, 471, 365, 365, 238,
            324, 288, 206, 324, 324, 500, 409,
            409, 273, 232, 273, 500, 570, 767,
            808, 685, 767, 685, 685,
          ],
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
            color: '#dee0e3',
            borderColor: '#646ace',
            borderWidth: 2
          },
          tooltip: {
            show: true
          },
          data: [
          732, 610, 610, 504, 504, 504, 349,
          349, 504, 342, 504, 610, 391, 192,
          154, 273, 191, 191, 126, 263, 349,
          252, 423, 622, 470, 532,
        ],
        }
      ]
    }
    lineGbuData.value = {
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
          symbolSize: 0,
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
                  color: 'rgba(153, 132, 255, .4)'
                },
                {
                  offset: 0.8,
                  color: 'rgba(255, 255, 255, 0)'
                }
              ])
            }
          },
          data: [
            540, 466, 540, 466, 385, 432, 334,
            334, 289, 289, 200, 289, 222, 289,
            289, 403, 554, 304, 289, 270, 134,
            270, 829, 344, 388, 364,
          ],
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
            color: '#dee0e3',
            borderColor: '#646ace',
            borderWidth: 2
          },
          tooltip: {
            show: true
          },
          data: [
            689, 562, 477, 477, 477, 477, 458,
            314, 430, 378, 430, 498, 642, 350,
            145, 145, 354, 260, 188, 188, 300,
            300, 282, 364, 660, 554,
          ],
        }
      ]
    }
  }, 1000)
})
</script>
