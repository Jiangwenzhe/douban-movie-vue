<template>
  <div id="app">
    <h1>hello world</h1>
    <Card></Card>
  </div>
</template>

<script>
import Card from './components/Card'
export default {
  name: 'app',
  components: {
    Card
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body{
    overflow: scroll;
    font-family: -apple-system,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Microsoft YaHei,Source Han Sans SC,Noto Sans CJK SC,WenQuanYi Micro Hei,sans-serif;
    font-size: 12px;
    line-height: 1.2;
    background-color: #F3F5F7;
    position: relative;
    background-size: 25px 25px;
    background-repeat:no-repeat;
    background-attachment:scroll;
  }

  a {
    text-decoration: none;
    color: #000;
  }

  .clearfix::after{
    content: '';
    display: block;
    clear: both;
  }

</style>
