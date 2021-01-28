<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h3 @click="increase">{{ count }}</h3>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted, onUpdated, onUnmounted } from 'vue'

export default defineComponent({
  name: 'About',
  setup () {
    const count = ref(0)
    const increase = (): void => {
      count.value++
    }
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
      count,
      increase
    }
  }
})
</script>
