<template>
  <div @click="itemClick">
    <!-- #ifdef H5 -->
    <!-- <svg class="lj-icon" :class="i" aria-hidden="true">
      <use :xlink:href="'#' + i"></use>
    </svg> -->
    <i class="i" :class="i"></i>
    <!-- #endif -->
    <!-- #ifndef H5 -->
    <view>
      <i class="i" :class="i"></i>
    </view>
    <!-- #endif -->
  </div>
</template>

<script>
import { IS_H5 } from 'lj-utils/microApi'
import { loadFile } from 'lj-utils'
export default {
  props: {
    i: {
      type: String,
      required: true,
    },
    // symbolUrl: {
    //   type: String,
    //   default: 'https://at.alicdn.com/t/c/font_2120237_p0vict17pzb.js',
    // },
  },
  mounted() {
    // #ifdef H5
    // 在线iconfont处理,h5使用symbol引入,不需要@import './iconfont.css';
    // loadFile(this.symbolUrl)
    // #endif
  },
  computed: {},
  methods: {
    itemClick() {
      !IS_H5 && this.$emit('click', this.item)
    },
  },
}
</script>

<style>
@import './iconfont.css';
.lj-icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
</style>
