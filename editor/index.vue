<template>
  <div class="component-editor">
    <div class='sty'>
      <span>样式：</span>
      <div class='list-type' v-for="(v, i) in titleStyleMap" :key="i" @click="chooseType(v.type)">
        <img :src="v.img" alt="">
        <div class="tip">{{v.des}}</div>
        <i class="el-icon-circle-check" v-if='v.type == num'></i>
      </div>
    </div>
    <el-form size="mini" label-width="100px">
      <el-form-item label="引言内容:">
        <el-input type="input" v-model="componentInfo.content" placeholder="请输入标题名称"></el-input>
      </el-form-item>
      <el-form-item label="文字大小:">
        <el-input placeholder="请输入文字大小" v-model="componentInfo.font" min='0' type='number'>
          <template slot="append">px</template>
        </el-input>
      </el-form-item>
      <el-form-item label="文字颜色:">
        <el-color-picker v-model="componentInfo.fontC" show-alpha></el-color-picker>
      </el-form-item>
      <el-form-item label="背景颜色:" v-if="num == 1">
        <el-color-picker v-model="componentInfo.baColor" show-alpha></el-color-picker>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
  export default {
    name: 'maliangeditor',
    props: {
      componentInfo: { // 固定字段，收集所有属性值
        type: [Object],
        default () {
          return {
            type: 2,
            content: ''
          }
        }
      }
    },
    data: function () {
      return {
        num: 1,
        titleStyleMap: [
          {
            type: 1,
            img: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/resource/ymm_1564480847580.png',
            des: '引言-1'
          },{
            type: 2,
            img: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/resource/ymm_1564480879985.png',
            des: '引言-2'
          },{
            type: 3,
            img: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/resource/ymm_1564480900535.png',
            des: '引言-3'
          },{
            type: 4,
            img: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/resource/ymm_1564480925360.png',
            des: '引言-4'
          },{
            type: 5,
            img: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/resource/ymm_1564480944636.png',
            des: '引言-5'
          },{
            type: 6,
            img: 'https://ymm-maliang.oss-cn-hangzhou.aliyuncs.com/ymm-maliang/resource/ymm_1564480967628.png',
            des: '引言-6'
          }
        ]
      }
    },
    computed: {
    },
    watch: {
      componentInfo: {
        hanlder: function (v) {
          console.log('editor index', v)
        },
      }
    },
    mounted: function () {
    },
    methods: {
      chooseType (type) {
        this.num = type
        this.componentInfo.type = type
        this.componentInfo.baColor = type == 1 ? '#f7f7f7' : '#fff'
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component-editor {
    .sty{
      // border 1px solid #ddd
      height 300px
      overflow hidden
      overflow-y auto
      margin-bottom 30px
      .list-type{
        margin-top 10px
        max-width 250px
        position relative
        border 1px solid #505152
        padding 10px
        border-radius 5px
        img{
          width 100%
        }
        i {
          position absolute
          right 10px
          bottom 15px
          font-size 22px
          color #409EFF
        }
        .tip{
          display: none
          width 100%
          position: absolute
          background-color: rgba(0, 0, 0, 0.7)
          text-align center
          font-size 12px
          padding 3px 0
          bottom 0
          left 0
          color #ccc
        }
        &:hover{
          .tip{
            display: block
          }
        }
      }
    }
  }
</style>
