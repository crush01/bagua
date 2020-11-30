<template>
  <view class="gua-container">
    <view
      v-for="(item, index) in guaArr"
      :key="index"
      @click="changeYao(item, index)"
      :class="['yao-item', {'yang': item === 1}, {'ying': item === 0}]"
    >
      <view class="ying-item"></view>
      <view class="ying-item"></view>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    guaArr: Array
  },
  data() {
    return {
      guaDate: []
    }
  },
  methods: {
    changeYao(yao, index) {
      // 点击改变卦象
      const currentYao = yao === 1 ? 0 : 1
      // const newGua = this.guaArr
      console.log('currentYao', currentYao)
      const newArr = this.guaArr
      newArr[index] = currentYao
      this.$emit('update:guaArr', newArr)
    }
  },
  mounted() {
    console.log('$guaDate', this.guaArr)
  }
}
</script>

<style lang="scss">
.gua-container {
  .yao-item {
    cursor: pointer;
    width: 400rpx;
    height: 20px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .ying-item {
      background-color: $gua-item-color;
      height: 100%;
      transition: width 0.6s;
    }
    &.yang {
      .ying-item {
        width: 50%;
      }
    }
    &.ying {
      .ying-item {
        width: 45%;
      }
    }
  }
}
</style>