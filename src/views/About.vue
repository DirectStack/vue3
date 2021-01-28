<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h3 @click="increase">{{ count }}</h3>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch, computed, onMounted, onUpdated, onUnmounted } from 'vue'

export default defineComponent({
  name: 'About',
  setup () {
    const count = ref(0)
    const increase = (): void => {
      count.value++
    }
    // watch
    watch(count, (newValue, oldValue) => {
      console.log('The new count value is: ' + count.value)
    })

    // computed
    const increaseCount = computed(() => {
      const newVal = count.value + 1
      return newVal
    })
    // 生命周期
    onMounted(() => {
      console.log('mounted vue3 typescript')
    })
    onUpdated(() => {
      console.log('updated vue3 typescript')
    })
    onUnmounted(() => {
      console.log('onUnmounted vue3 typescript')
    })
    // 暴露给模板
    return {
      increaseCount,
      count,
      increase
    }
  }
})
</script>
