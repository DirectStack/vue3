<template>
  <div class="user">
    <h1>{{ user.name }}</h1>
    <h1>{{ user.age }}</h1>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'User',
  async setup (props: any) {
    const fetchUser = () => {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve({ name: 'Carlo', age: 20 })
        }, 3000)
      })
    }

    const user = await fetchUser()
    return { user }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0
}
ul {
  list-style-type: none;
  padding: 0
}
li {
  display: inline-block;
  margin: 0 10px
}
a {
  color: #42b983
}
</style>
