<template>
  <div class="home">
    <HelloWorld v-bind:msgs="msgs" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  props: {
    msgs: Array
  },
  components: {
    HelloWorld
  }
}
</script>
