<template>
  <div class="component-editor">
    <el-form ref="form" label-width="80px" label-position='left' size='mini'>
      <el-form-item label="文字:">
        <el-input v-model="componentInfo.text" placeholder="请输入按钮文字"></el-input>
      </el-form-item>
      <el-form-item label="链接:">
        <el-input v-model="componentInfo.url" placeholder="请输入链接"></el-input>
      </el-form-item>
      <el-form-item label="文字颜色:">
        <el-color-picker v-model="componentInfo.color" show-alpha></el-color-picker>
        <span style='vertical-align: top'>{{componentInfo.color}}</span>
      </el-form-item>
      <el-form-item label="背景色:">
        <el-color-picker v-model="componentInfo.backgroundColor" show-alpha></el-color-picker>
        <span style='vertical-align: top'>{{componentInfo.backgroundColor}}</span>
      </el-form-item>
      <el-form-item label="圆角:">
        <el-input placeholder="请输入圆角大小" v-model.number="componentInfo.radius" type='number' min='0'>
          <template slot="append">px</template>
        </el-input>
      </el-form-item>
      <el-form-item label="边框:">
        <el-input placeholder="请输入边框大小" v-model="componentInfo.border" min='0' type='number'>
          <template slot="append">px</template>
        </el-input>
      </el-form-item>
      <el-form-item label="边框颜色:">
        <el-color-picker v-model="componentInfo.borderColor" show-alpha></el-color-picker>
        <span style='vertical-align: top'>{{componentInfo.borderColor}}</span>
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
            text: '提交',
            color: 'rgb(255, 255, 255)',
            url: '',
            radius: '3',
            border: '0',
            borderColor: '',
            backgroundColor: 'rgb(2, 181, 136)'
          }
        }
      }
    },
    data: function () {
      return {
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
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component-editor {
    .box-card {
      background #262626
      color: #ccc;
    }
    .btn-type{
      max-width 300px
      position relative
      img{
        max-width: 300px
      }
      i {
        position: absolute;
        right: 0px;
        top: 0px;
        color #67C23A
      }
      .tip{
        display: none
        position absolute
        width: 100%
        text-align: center
        font-size: 10px
        bottom 0
        left 0
        background rgba(0, 0, 0, 0.7)
        color: #ececec
        height: 25px;
        line-height: 25px;
      }
      &:hover{
        .tip{
          display block
        }
      }
    }
  }
</style>
