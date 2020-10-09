<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img class="banner-img" :src="bannerImg"/>
            <div class="banner-info">
                <div class="banner-title">
                    {{this.sightName}}
                </div>
                <div class="banner-number">
                    <span class="iconfont">&#xe635;</span>
                    {{this.bannerImgs.length}}
                </div>
            </div>
        </div>
        <fade-animation>
          <common-gallary
          :imgs="bannerImgs"
          v-show="showGallary"
          @close="handleGallaryClose">
          </common-gallary>
        </fade-animation>
    </div>
</template>

<script>
import CommonGallary from 'common/gallary/gallary'
import fadeAnimation from 'common/fade/fadeAnimation'
export default {
  name: 'DetailBaner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
  },
  components: {
    CommonGallary,
    fadeAnimation
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      color: #fff
      display: flex
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-title
        flex: 1
        font-size: .42rem
        padding: 0 .4rem
      .banner-number
        padding: 0 .4rem
        line-height: .4rem
        height: .32rem
        margin-top: .14rem
        font-size: .24rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        .banner-iconfont
          font-sie: .24rem
</style>
