<template>
<div>
  <main>
    <transition name="fade">
      <keep-alive>
        <component :is="currentTab"></component>
      </keep-alive>
    </transition>
  </main>
  <footer class="backdrop-blur">
    <div :class="[currentTab === 'Top250' ? 'active' : null]" @click="toggleTab('Top250')">
      <span class="iconfont icon-paihangbang"></span>
      <span>排行榜</span>
    </div>
    <div :class="[currentTab === 'InTheater' ? 'active' : null]" @click="toggleTab('InTheater')">
      <span class="iconfont icon-dianying"></span>
      <span>正在上映</span>
    </div>
    <div :class="[currentTab === 'SearchMovie' ? 'active' : null]" @click="toggleTab('SearchMovie')">
      <span class="iconfont icon-search"></span>
      <span>搜索</span>
    </div>
  </footer>
</div>
</template>

<script>
import Top250 from './Top250'
import InTheater from './InTheater'
import SearchMovie from './SearchMovie'
export default {
  name: 'Tabs',
  components: {
    Top250,
    InTheater,
    SearchMovie
  },
  data() {
    return {
      currentTab: 'Top250'
    }
  },
  methods: {
    toggleTab: function(tab) {
      this.currentTab = tab
    }
  }
}
</script>

<style lang="scss" scoped>
// main
main {
  height: 100%;
  overflow: scroll;
  -webkit-overflow-scrolling: touch;
  .fade-enter-active, .fade-leave-active {
    transition: opacity .4s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
}

// footer
footer {
  position: fixed;
  bottom: 0px;
  padding: 5px;
  width: 95%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  &.backdrop-blur {
    background-color: rgba(255, 255, 255, 1);
  }
  @supports ((-webkit-backdrop-filter: blur(2em)) or (backdrop-filter: blur(2em))) {
    &.backdrop-blur {
      background-color: rgba(255, 255, 255, .5);
      -webkit-backdrop-filter: blur(2em);
      backdrop-filter: blur(2em);
    }
  }
  div {
    flex: 1;
    text-align: center;
    span {
      display: block;
      font-size: 12px;
      &.iconfont {
        font-size: 21px;
      }
    }
  }
  .active {
    color:#00B51D;
  }
}
</style>
