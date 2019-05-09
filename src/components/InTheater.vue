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
      title: '',
      url: 'https://api.douban.com/v2/movie/in_theaters',
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
  },
  deactivated() {
    this.setScrollPosition()
    console.log(this.scrollPosition)
  }
}
</script>

<style>

</style>
