<template>
  <Panel
    :title="title"
    :requestURL=url
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
      title: 'InTheater',
      url: 'https://api.douban.com/v2/movie/in_theaters'
    }
  }
}
</script>

<style>

</style>
