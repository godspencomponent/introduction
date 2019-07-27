<template>
  <div class="component-editor">
    <el-form size="mini" label-width="100px">
      <el-form-item label="选择种类:">
        <div class="sty">
          <div class="imgSty" v-for="i in titleStyleMap" :key="i.type" @click="chooseType(i.type)">
            <img :src="i.img" alt="">
          </div>
        </div>
      </el-form-item>
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
            img: '../src/assets/pic1.png'
          },{
            type: 2,
            img: '../src/assets/pic2.png'
          },{
            type: 3,
            img: '../src/assets/pic3.png'
          },{
            type: 4,
            img: '../src/assets/pic4.png'
          },{
            type: 5,
            img: '../src/assets/pic5.png'
          },{
            type: 6,
            img: '../src/assets/pic6.png'
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
      height 250px
      overflow hidden
      overflow-y auto
      .imgSty {
        width 400px
        height 80px
        cursor pointer
        margin-bottom 10px
        img {
          height 100%
        }
      }
    }
  }
</style>
