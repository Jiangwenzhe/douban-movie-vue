<template>
  <div>
    <h1>{{ title }}</h1>
    <Card
      v-for="(data, index) in panel_data.subjects"
      :key="index"
      :movie_data="data"
    ></Card>
  </div>
</template>
<script>
import Card from './Card'
import in_theater from './../assets/in_theater.json'

export default {
  name: 'Panel',
  props: {
    title: {
      type: String,
      default: "In_theater"
    },
    requestURL:{

    }
  },
  components: {
    Card
  },
  data() {
    return {
      panel_data: {}
    }
  },
  methods() {

  },
  mounted() {
    this.panel_data = in_theater
  }
}
</script>

<style>

</style>
