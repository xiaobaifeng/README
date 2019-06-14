<template>
  <div class="com-score">
    <div class="com-score__inner">
      <div class="com-score__text" :style="{
        color: color
      }">
        <slot name="label"></slot>
        <span v-if="!$slots.label">
          得分:
        </span>
        <span :style="{paddingLeft: `${spacing}px`}">
          <span v-if="!$slots['value']">
            {{ value }}
          </span>
          <slot name="value"></slot>
        </span>分
      </div>
      <div
        v-if="iconScore && value >= 0"
        class="com-score__icons"
        :style="{paddingLeft: `${spacing}px`}">
        <i
          class="com-score__icons__item"
          v-for="(src, index) in curScoreIconSrcs"
          :key="index"
          :style="{
            backgroundImage: `url(${src})`
          }"></i>
      </div>
    </div>
  </div>
</template>
<script>
import xiaolian from '@/assets/images/expression-icon/xiaolian.png'
import ziya from '@/assets/images/expression-icon/ziya.png'
import jingya from '@/assets/images/expression-icon/jingya.png'
import nanguo from '@/assets/images/expression-icon/nanguo.png'
import liulei from '@/assets/images/expression-icon/liulei.png'
import shuai from '@/assets/images/expression-icon/shuai.png'

export default {
  props: {
    value: {
      type: Number
    },
    iconScore: {
      type: Boolean,
      default: false
    },
    spacing: {
      type: Number,
      default: 20
    },
    color: {
      type: String,
      default: '#000000'
    }
  },
  data () {
    return {
      scoreIconSrcOpts: [
        {
          src: shuai,
          value: 0
        },
        {
          src: liulei,
          value: 1
        },
        {
          src: nanguo,
          value: 2
        },
        {
          src: jingya,
          value: 5
        },
        {
          src: ziya,
          value: 10
        },
        {
          src: xiaolian,
          value: 20
        }
      ]
    }
  },
  computed: {
    curScoreIconSrcs () {
      const getSrcByValue = (value) => this.scoreIconSrcOpts.filter(opt => opt.value === value)[0].src
      if (this.value === 0) {
        return [getSrcByValue(0)]
      }
      let resArr = []
      let curValue = this.value
      this.scoreIconSrcOpts.map(({ value }) => value)
        .sort((a, b) => b - a)
        .forEach(val => {
          if (curValue === 0) return
          let quotient = Math.floor(curValue / val)
          const remainder = curValue % val
          while (quotient > 0) {
            resArr.push(getSrcByValue(val))
            quotient--
          }
          curValue = remainder
        })
      return resArr
    }
  }
}
</script>
<style lang="less" scoped type="text/css">
  .com-score{
    display: inline-block;
    &__inner{
      display: flex;
      align-items: flex-start;
    }
    &__text{
      line-height: 24px;
    }
    &__icons{
      flex-grow: 1;
      line-height: 0;
      &__item{
        display: inline-block;
        width: 24px;
        height: 24px;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: 0 0;
      }
      &__item + &__item{
        margin-left: 10px;
      }
    }
  }
</style>
