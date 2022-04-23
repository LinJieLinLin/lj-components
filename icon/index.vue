<template>
  <div>
    <!-- #ifdef H5 -->
    <svg class="lj-icon" :class="i" aria-hidden="true">
      <use :xlink:href="'#' + i"></use>
    </svg>
    <!-- #endif -->
    <!-- #ifndef H5 -->
    <view>
      <i class="i" :class="i"></i>
    </view>
    <!-- #endif -->
  </div>
</template>

<script>
if (process.env.NODE_ENV === 'development') {
  // #ifdef H5
  import('./iconfont')
  // #endif
}
export default {
  props: {
    i: {
      type: String,
      required: true
    }
  },
  computed: {
  }
}
</script>

<style>
/* #ifndef H5 */
@import './iconfont.css';

/* #endif */
.lj-icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
</style>