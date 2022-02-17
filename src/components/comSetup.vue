<template>
  <div>
    <h3 :style="{ color: titleInfo.color }">{{ titleInfo.value }}</h3>
    {{ counter }}
  </div>
  <div>{{ doubleCounter }}</div>
  <input v-model="value" @keyup.enter="addTodo(value)">
  <div v-for="item in todos">{{ item.name }}</div>
</template>

<script lang='ts' setup>
import { ref, PropType, computed, defineProps } from 'vue'
interface Todo {
  id: number,
  name: string,
  completed: boolean
}
interface TitleInfo {
  value: string,
  color: string
}
const counter = ref(1)
const value = ref()
const doubleCounter = computed(() => counter.value*2)
const todos = ref([] as Todo[])
todos.value.push({
      id: 1,
      name: 'sb',
      completed: true
})
const addTodo = (val: any): void => {
      todos.value.push({
        id: todos.value.length+1,
        name: val,
        completed: false
      })
      value.value = ''
}
defineProps({
  titleInfo: {
      type: Object as PropType<TitleInfo>,
      required: true
    }
})
</script>

<style>
</style>