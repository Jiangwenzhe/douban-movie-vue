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
import jsonp from 'jsonp'

export default {
  name: 'Panel',
  props: {
    title: {
      type: String,
      default: "In_theater"
    },
    requestURL:{
      type: String,
      default: null
    }
  },
  components: {
    Card
  },
  data() {
    return {
      panel_data: {},
      start: 0,
      count: 20,
      hasMore: true
    }
  },
  methods: {
    getMovieData: function(url) {
      console.log(url)
      if(this.hasMore) {
        jsonp(url, null, (error, data) => {
          if(error) {
            console.log(error)
          } else  {
            this.start += this.count
            console.log(data.subjects)
            if(data.total < this.start){
              this.hasMore = false
            }
          }
        })
      } else {
        console.log('此页码数据请求完了')
      }
    }
  },
  mounted() {
    this.getMovieData(`${this.requestURL}?start=${this.start}&count=${this.count}`)
    this.panel_data = in_theater
  }
}
</script>

<style>

</style>
