<template>
  <div v-if="errMsg"> {{ errMsg }} </div>
  <Suspense v-else>
    <template #default>
      <User/>
    </template>
    <template #fallback>
      <div>正在拼了命的加载…</div>
    </template>
  </Suspense>
</template>
<script lang="ts">
import { defineComponent, onErrorCaptured, ref } from 'vue'
import User from '@/components/User.vue' // @ is an alias to /src

export default defineComponent({
  name: 'Async',
  components: {
    User
  },
  setup () {
    const errMsg = ref('')

    onErrorCaptured(e => {
      errMsg.value = '呃，出了点问题！'
      console.log(e)
      // 不拦截异常
      return true
    })

    return {
      errMsg
    }
  }
})
</script>
