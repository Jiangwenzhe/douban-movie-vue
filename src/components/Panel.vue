<template>
  <div>
    <h1>{{ title }}</h1>
    <Card
      v-for="(data, index) in panel_data"
      :key="index"
      :movie_data="data"
    ></Card>
    <div v-if="hasMore" class="loading"><span class="iconfont icon-jiazai_dan"></span></div>
    <div v-if="!hasMore" class="bottom-tip">-----没有数据啦-----</div>
  </div>
</template>
<script>
import Card from './Card'
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
      panel_data: [],
      start: 0,
      count: 20,
      hasMore: true,
      scrolledToBottom: false,
    }
  },
  methods: {

    handleScroll(){
        let scrollPosition_Y = Math.max(window.pageYOffset, document.documentElement.scrollTop, document.body.scrollTop)
        let bottomOfWindow = scrollPosition_Y + window.innerHeight === document.documentElement.offsetHeight
        if (bottomOfWindow) {
         this.scrolledToBottom = true
         console.log('--- at buttom ---')
         console.log('------', this.title, '----获取到数据')
         this.getMovieData(`${this.requestURL}?start=${this.start}&count=${this.count}`)
        }
        this.scrolledToBottom = false
    },
    getMovieData(url) {
      console.log(url)
      if(this.hasMore) {
        jsonp(url, null, (error, data) => {
          if(error) {
            console.log(error)
          } else  {
            this.start += this.count
            console.log(data.subjects)
            this.panel_data = Array.from(new Set(this.panel_data.concat(data.subjects)))
            console.log(this.panel_data)
            if(data.total < this.start){
              this.hasMore = false
            }
          }
        })
      } else {
        console.log(`在${this.title}中的数据请求完了`)
      }
    }
  },
  mounted() {
    this.getMovieData(`${this.requestURL}?start=${this.start}&count=${this.count}`)
  },
  activated() {
    console.log('--- enter ----', this.title)
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated() {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="scss" scoped>
  .loading {
    text-align: center;
    font-size: 16px;
    @keyframes rotate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    .iconfont {
      display: inline-block;
      animation: .7s rotate linear infinite;
    }
  }
  .bottom-tip {
    text-align: center;
    font-size: 12px;
    margin-bottom: 5px;
    font-weight: bold;
  }
</style>
