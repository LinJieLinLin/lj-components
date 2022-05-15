<!--
 * @Author: linj
 * @Email: 993353454@qq.com
 * @Date: 2020-11-26 17:01:01
 * @Description:
-->
<template>
  <div class="item-list flex b-1px" :class="{ 'disabled': item.disabled }" @click="itemClick">
    <slot name="header">
      <div class="flex0 text-l-1">
        <div>{{ item.name }}</div>
      </div>
    </slot>
    <slot name="body">
      <div class="flex1">
      </div>
    </slot>
    <slot name="footer">
      <Icon i="i-arrow-right" v-if="!c.hideArrow && !item.hideArrow" class="fs-20 flex0"></Icon>
    </slot>
  </div>
</template>

<script>
import Icon from '../../icon/index'
import { IS_H5 } from 'lj-utils/microApi'

export default {
  props: {
    item: {
      type: Object,
      default: function () {
        return {}
      }
    },
    c: {
      type: Object,
      default: function () {
        return {}
      }
    }
  },
  components: {
    Icon
  },
  mounted() {

  },
  computed: {

  },
  data() {
    return {

    }
  },
  methods: {
    itemClick() {
      if (!this.item.disabled) {
        !IS_H5 && this.$emit('click', this.item)
      }
    }
  },
}
</script>

<style scoped lang="scss">
$pdWidth: 16px;

.item-list {
  position: relative;
  padding-left: $pdWidth;
  padding-right: $pdWidth;
  height: 44px;
  @include iFlex();
  @include iFlex(flex-middle);
  @include iBtnBgColor(#fff);
  box-sizing: border-box;

  &::before {
    content: '';
    position: absolute;
    left: $pdWidth;
    right: $pdWidth;
  }
}
</style>
