<template>
  <div>
    <h3 :style="{ color: titleInfo.color }">{{ titleInfo.value }}</h3>
    {{ counter }}
  </div>
  <div>{{ doubleCounter }}</div>
  <input v-model="value" @keyup.enter="addTodo(value)">
  <div v-for="item in todos">{{ item.name }}</div>
</template>

<script lang='ts'>
import { ref, defineComponent, PropType } from 'vue'
interface Todo {
  id: number,
  name: string,
  completed: boolean
}
interface TitleInfo {
  value: string,
  color: string
}
export default defineComponent({
  props: {
    titleInfo: {
      type: Object as PropType<TitleInfo>,
      required: true
    }
  },
  data() {
    return {
      todos: [] as Todo[],
      value: ''
    }
  },
  created() {
    this.todos.push({
      id: 1,
      name: 'sb',
      completed: true
    })
  },
  methods: {
    addTodo(val: any): void {
      this.todos.push({
        id: this.todos.length+1,
        name: val,
        completed: false
      })
      this.value = ''
      console.log(this.todos)
    }
  },
  computed: {
    doubleCounter(): number {
      return this.counter * 2
    }
  },
  setup() {
    const counter = ref(1)
    return {
      counter
    }
  }
})
</script>

<style>
</style>