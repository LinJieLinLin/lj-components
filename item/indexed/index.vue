<template>
  <view>
    <view v-if="loaded || list.itemIndex < 15" class="uni-indexed-list__title-wrapper">
      <text v-if="list.items && list.items.length > 0" class="uni-indexed-list__title">
        {{ list.key }}
      </text>
    </view>
    <view v-if="(loaded || list.itemIndex < 15) && list.items && list.items.length > 0" class="uni-indexed-list__list">
      <view v-for="(item, index) in list.items" :key="index" class="uni-indexed-list__item">
        <view class="uni-indexed-list__item-container" @click="onClick(idx, index)">
          <view class="uni-indexed-list__item-border"
            :class="{ 'uni-indexed-list__item-border--last': index === list.items.length - 1 }">
            <view v-if="showSelect" style="margin-right: 20rpx;">
              <!--ljTodo 2022-05-04 01:24:30 -->
              <radio />
            </view>
            <text class="uni-indexed-list__item-content">{{ item.name }}</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    loaded: {
      type: Boolean,
      default: false
    },
    idx: {
      type: Number,
      default: 0
    },
    list: {
      type: Object,
      default() {
        return {}
      }
    },
    showSelect: {
      type: Boolean,
      default: false
    }
  },
  components: {

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
    onClick(idx, index) {
      this.$emit('itemClick', {
        idx,
        index
      })
    }
  },
}
</script>

<style scoped lang="scss">
.uni-indexed-list__list {
  background-color: $uni-bg-color;
  display: flex;
  flex-direction: column;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: $uni-border-color;
}

.uni-indexed-list__item {
  font-size: $uni-font-size-lg;
  display: flex;
  flex: 1;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.uni-indexed-list__item-container {
  padding-left: $uni-spacing-row-lg;
  flex: 1;
  position: relative;
  display: flex;
  box-sizing: border-box;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.uni-indexed-list__item-border {
  flex: 1;
  position: relative;
  display: flex;
  box-sizing: border-box;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  height: 50px;
  padding: $uni-spacing-row-lg;
  padding-left: 0;
  border-bottom-style: solid;
  border-bottom-width: 1px;
  border-bottom-color: $uni-border-color;
}

.uni-indexed-list__item-border--last {
  border-bottom-width: 0px;
}

.uni-indexed-list__item-content {
  flex: 1;
  font-size: 14px;
}

.uni-indexed-list {
  display: flex;
  flex-direction: row;
}

.uni-indexed-list__title-wrapper {
  display: flex;
  width: 100%;
  background-color: #f7f7f7;
}

.uni-indexed-list__title {
  padding: 6px 12px;
  line-height: 24px;
  font-size: $uni-font-size-sm;
}
</style>
