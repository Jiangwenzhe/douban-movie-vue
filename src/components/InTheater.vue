<template>
  <Panel
    title="title"
    requestURL="https://api.douban.com/v2/movie/in_theaters"
  ></Panel>
</template>

<script>
import Panel from './Panel'
export default {
  name: 'InTheater',
  components: {
    Panel,
  },
  data() {
    return {
      title: 'InTheater'
    }
  }
}
</script>

<style>

</style>
