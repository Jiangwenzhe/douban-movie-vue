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
      title: 'Top2501',
      url: 'https://api.douban.com/v2/movie/top250',
      scrollPosition: 0
    }
  },
  methods: {
    setScrollPosition() {
      this.scrollPosition =  document.documentElement.scrollTop
    }
  },
  activated() {
    console.log(this.title)
    document.documentElement.scrollTop = this.scrollPosition
    console.log(document.documentElement.scrollTop)
  },
  deactivated() {
    this.setScrollPosition()
    console.log(this.scrollPosition)
  }
}
</script>

<style>

</style>
