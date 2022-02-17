<template>
  <div class="box">
    <div
      :id="chartId"
      class="echart-box"
      :class="className"
      :style="{ height: height, width: width }"
    ></div>
    <div class="select" v-if="showSelect">
      <select>
        <option value="1">1</option>
        <option value="2">2</option>
      </select>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { toRefs, watch, onMounted, computed } from "vue";
import * as echarts from "echarts";
import { GridComponent, GridComponentOption } from 'echarts/components';
import { LineChart, LineSeriesOption } from 'echarts/charts';
import { UniversalTransition } from 'echarts/features';
import { CanvasRenderer } from 'echarts/renderers';

echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition]);

type EChartsOption = echarts.ComposeOption<
  GridComponentOption | LineSeriesOption
>;
const props = defineProps({
  chartId: {
    type: String,
    default: () => "line-chart"
  },
  showSelect: {
    type: Boolean,
    default: true
  },
  className: {
    type: String,
    default: () => "line-chart"
  },
  height: {
    type: String,
    default: "100%",
  },
  width: {
    type: String,
    default: "100%",
  },
  options: {
    type: Object,
    default: () => ({})
  }
})
const { options } = toRefs(props);
// 配置信息
const setOptions = computed((): EChartsOption => {
  let option = options.value
  return option;
});
// 创建图表
function initChart() {
  let chartDom = document.getElementById(props.chartId);
  if (chartDom) {
    let myChart = echarts.init(chartDom);
    myChart.setOption(setOptions.value);
    window.onresize = function () {
      //自适应大小
      myChart.resize();
    };
  }
}
onMounted(() => {
  initChart();
});
// 监听传值，刷新图表
watch(options, () => {
  initChart();
}, { deep: true });
</script>

<style>
.box {
  position: relative;
}
.select {
  position: absolute;
  top: 50px;
  left: 50%;
}
</style>