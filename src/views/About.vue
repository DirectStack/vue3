<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h3 @click="increase">{{ count }}</h3>
    <HelloWorld msg="msg"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch, computed, provide, reactive, onMounted, onUpdated, onUnmounted } from 'vue'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

export default defineComponent({
  name: 'About',
  components: {
    HelloWorld
  },
  setup () {
    // ref基本数据类型
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

    // provide
    // reactive引用类型
    const geolocation = reactive({
      longitude: 90,
      latitude: 135
    })
    provide('geolocation', geolocation)

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
