<template>
  <div class="component">
    <div class="comp">
      <div class="fd-foreword" :class="{fd_border: type == 5}">
        <div class="fd-foreword-left">
          <img :src="iconType" alt="" :class="{imgType5: type == 5}">
        </div>
        <div class="comp_quote_1-left-line" v-if="type == 2"></div>
        <div class="fd-foreword-body">
          <div :class="classObject" class="text" :style="{backgroundColor: baColor,fontSize: font + 'px',color: fontC}">
            <p v-if="type == 6">
              <span v-for="(v, i) in content" :key="i">{{v}}</span>
            </p>
            <p v-else>{{content}}</p>
          </div>
        </div>
        <div class="fd-foreword-right" v-if="type == 4">
          <img src="./assets/icon4_bottom.png" alt="" class="">
        </div>
      </div> 
    </div>
  </div>
</template>

<script>
  import {VueExtend} from 'godspen-lib'

  export default {
    mixins: [VueExtend.mixin],
    name: 'introduction',
    label: process.env.LABEL,
    style: process.env.STYLE,
    props: {
      type: {
        type: Number,
        default: 1,
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      content: {
        type: String,
        default: '',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      baColor: {
        type: String,
        default: '',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      font: {
        type: String,
        default: '14',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      fontC: {
        type: String,
        default: '#999',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
    },
    computed: {
      iconType () {
        return {
          1: require('./assets/icon1.png'),
          2: require('./assets/icon2.png'),
          3: require('./assets/icon3.png'),
          4: require('./assets/icon4_top.png'),
          5: require('./assets/icon5.png'),
          6: require('./assets/icon1.png'),
        }[this.type]
      },
      classObject () {
        return {
          1: 'text1',
          2: 'text2',
          3: 'text3',
          4: 'text4',
          5: 'text5',
          6: 'text6',
        }[this.type]
      }
    },
    editorMethods: {
    },
    methods: {
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component {
    width 100%
    height 110px
    .comp {
      width 100%
      height 110px
      padding 8px 16px
      .fd_border {
        border: 1px solid #000;
      }
      .fd-foreword {
        padding 0 10px 0 36px
        position relative
        p {
          margin 0
        }
        .fd-foreword-left {
          position absolute
          left 0
          top 0
          img {
            width 18px
            height 18px
          }
        }
        .fd-foreword-right {
          position absolute
          bottom 0
          right 0
          img {
            width 18px
            height 18px
          }
        }
        .comp_quote_1-left-line {
          position: absolute;
          width: 3px;
          top: 24px;
          left 10px
          bottom: 0;
          transform: translateX(-50%);
          background: #e9e9e9;
        }
        .text {
          font-size: 14px;
        }
        .text1 {
          display: block;
          padding: 8px 9px;
          color: #999;
          background: #f7f7f7;
        }
        .text2, .text3 {
          color: #999;
        }
        .text4 {
          color: #333;
        }
        .text5 {
          color: #333;
          padding 8px 0
        }
        .text6 {
          span {
            background-image: linear-gradient(180deg,transparent 60%,#fff566 0);
          }
        }
        .imgType5 {
          background-color #000
        }
      }
    }
  }
</style>
