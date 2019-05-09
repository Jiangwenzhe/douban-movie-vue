<template>
  <div>
    <div id="search">
      <div class="search-area">
        <input type="text" v-model="inputValue"  placeholder="搜索电影" />
        <span class="button" id="searchBtn" @click="handleInput"> 搜索</span>
      </div>
    </div>
    <Panel v-if="url" :requestURL=url :title="title"></Panel>
  </div>
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
      title: '',
      inputValue: '',
      url: ''
    }
  },
  methods: {
    handleInput() {
      console.log(this.inputValue)
      this.url = `https://api.douban.com/v2/movie/search?q=${this.inputValue}`
    }
  }
}
</script>

<style lang="scss" scoped>
  #search {
    height: calc(100% - 45px);
    .search-area{
      padding: 8px;
      width: calc(100vw - 24px);
      margin: 10px auto;
      color: #333;
      position: relative;
      border-radius: 10px;
      background: #fefefe;
      box-shadow: 0 2px 5px 0 rgba(217,221,225,.3);
      input {
        font-size: 16px;
        width: calc(100% - 58px);
        padding: 12px;
        border-radius: 8px;
        background-color: #F3F5F7;
        border: none;
        box-shadow: none;
        outline: none;
      }
      .button{
        font-size: 16px;
        position: absolute;
        right: 6px ;
        padding: 11px 10px;
        background: #00B51D;
        color: #fff;
        border-radius: 8px;
        cursor: pointer;
      }
    }

  }
</style>