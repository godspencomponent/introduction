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
            img: 'https://gw.alipayobjects.com/os/q/cms/images/jnlh8d66/e28ad88e-48a1-4c2a-af63-d24f3443d8cd.cms/images/fff86f5d-e206-4ffb-8d8a-a8df90207242.png?x-oss-process=image/resize,w_560/crop,h_560'
          },{
            type: 2,
            img: 'https://gw.alipayobjects.com/os/q/cms/images/jnlh85i0/fb89e9e1-9bbf-4052-9f01-ebab6e6cdf77.cms/images/96c50b7a-fb2b-4950-bcdc-8aca26498319.png?x-oss-process=image/resize,w_560/crop,h_560'
          },{
            type: 3,
            img: 'https://gw.alipayobjects.com/os/q/cms/images/jnlh4gn0/c6a4c09d-5820-45bd-847e-80ed80157070.cms/images/997a825b-28ad-493b-ad2c-6829e0f08711.png?x-oss-process=image/resize,w_560/crop,h_560'
          },{
            type: 4,
            img: 'https://gw.alipayobjects.com/os/q/cms/images/jnlh4b9s/61a76512-cfab-4af4-8999-4de4b8d80ecb.cms/images/a9e8f44e-20a5-45f4-9a9b-994a94c21f1a.png?x-oss-process=image/resize,w_560/crop,h_560'
          },{
            type: 5,
            img: 'https://gw.alipayobjects.com/os/q/cms/images/jnlh46ci/464c75d9-8c5b-4fad-ab2b-b5868d7237d2.cms/images/da4fca2a-046d-43e3-a669-cc653b2d8dec.png?x-oss-process=image/resize,w_560/crop,h_560'
          },{
            type: 6,
            img: 'https://gw.alipayobjects.com/os/q/cms/images/jnlh41g2/1f5a5a3d-e376-4b21-9afa-3794d0c59530.cms/images/62971d54-b849-468f-93e6-fee52a3f464a.png?x-oss-process=image/resize,w_560/crop,h_560'
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
