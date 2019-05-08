<template>
  <div class="card">
    <a :href="movie_info.alt">
      <div class="cover">
        <img :src="movie_info.images.medium">
      </div>
      <div class="detail">
        <h2>{{ movie_info.title }}</h2>
        <div class="extra">
          <span class="score">{{ movie_info.rating.average }}</span>&nbsp;/&nbsp;
          <span class="collection">{{ movie_info.collect_count}}</span>&nbsp;收藏
        </div>
        <div class="extra">
          <span class="year">{{ movie_info.year }}</span>&nbsp;/&nbsp;
          <span class="type">{{ movie_info.genres.join('、')}}</span>
        </div>
        <div class="extra">
          <span class="director">
            导演：{{ movie_info.directors.map(i => i.name).join('、') }}
          </span>
        </div>
        <div class="extra">
          <div class="casts">
            演员：{{ movie_info.casts.map(i => i.name).join('、')}}
          </div>
        </div>
      </div>
    </a>
  </div>
</template>

<script>
import info from './../assets/single_movie.json'
export default {
  name: 'Card',
  props: {
    movie_data: {
      type: Object,
      default: function() {
        return info
      }
    }
  },
  data() {
    return {
      movie_info: this.movie_data
    }
  },
}
</script>

<style lang="scss" scoped>
  .card {
    width: calc(100vw - 24px);
    border-radius: 15px;
    margin: 10px auto;
    padding: 10px;
    background: #fefefe;
    box-shadow: 0 2px 5px 0 rgba(217,221,225,.3);
    a {
      display: flex;
    }
    .cover {
      img {
        border-radius: 10px;
        width: 70px;
        box-shadow: 0 2px 3px 0 rgba(0,0,0,0.2);
      }
    }
    .detail {
      flex: 1;
      padding-left: 10px;
      h2 {
        font-size: 16px;
      }
      .extra {
        color: #999;
        margin-top: 4px;
      }
      .score {
        color: #FF5722;
        font-weight: bold;
      }
    }

  }
</style>
