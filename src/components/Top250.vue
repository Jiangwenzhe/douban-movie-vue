<template>
  <Panel
    :title="title"
    :requestURL=url
  ></Panel>
</template>

<script>
import Panel from './Panel'
export default {
  name: 'Top250',
  components: {
    Panel
  },
  data() {
    return {
      title: 'Top250',
      url: 'https://api.douban.com/v2/movie/top250'
    }
  }
}
</script>

<style>

</style>
