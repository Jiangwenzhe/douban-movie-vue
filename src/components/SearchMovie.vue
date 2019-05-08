<template>
  <Panel :title="title"></Panel>
</template>

<script>
import Panel from './Panel'
export default {
  name: 'SearchMovie',
  components: {
    Panel,
  },
  data() {
    return {
      title: 'Search'
    }
  }
}
</script>

<style>

</style>