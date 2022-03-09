<template>
  <!-- <EchartsDemo :xAxisData="chartData.xAxisData" :seriesData="chartData.seriesData" height="500px"></EchartsDemo> -->
  <div>
  <el-row class="mb-4">
    <el-button>Default</el-button>
    <el-button type="primary">Primary</el-button>
    <el-button type="success">Success</el-button>
    <el-button type="info">Info</el-button>
    <el-button type="warning">Warning</el-button>
    <el-button type="danger">Danger</el-button>
    <el-button>中文</el-button>
  </el-row>
</div>
  <EchartsDemo chartId="left-echart" :options="chartData" height="500px"></EchartsDemo>
  <EchartsDemo chartId="right-echart" :showSelect="false" :options="chartDataRight" height="300px"></EchartsDemo>
  <ComSetup :title-info="{ value: '笨蛋', color: 'red' }"></ComSetup>
</template>s

<script lang="ts" setup>
import { onMounted, ref } from 'vue'
import ComSetup from '../../components/comSetup.vue';
import EchartsDemo from '../../components/echartsDemo.vue'
const chartData = ref();
const chartDataRight = ref();
onMounted(() => {
  chartData.value = {
    xAxis: {
      type: 'category',
      data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    yAxis: {
      type: 'value'
    },
    series: [
      {
        data: [150, 230, 224, 218, 135, 147, 260],
        type: 'line'
      }
    ]
  }
  chartDataRight.value = {
    xAxis: {
      type: 'category',
      data: ['Mon', 'Tue', 'Wed', 'Thu']
    },
    yAxis: {
      type: 'value'
    },
    series: [
      {
        data: [820, 932, 901, 934],
        type: 'line',
        smooth: true
      }
    ]
  }
})
</script>

<style>
</style>
