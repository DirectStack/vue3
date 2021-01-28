<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>
<script lang="ts">
import { Options, Vue } from 'vue-class-component'
console.log(1111111111111)
@Options({
  props: {
    msg: String
  }
})
export default class HelloWorld extends Vue {
    msg!: string
}
</script>
