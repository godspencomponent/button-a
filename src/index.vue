<template>
  <div class="component" :style='sty' @click='jump'>
    {{ctext}}
  </div>
</template>

<script>
  import {VueExtend} from 'godspen-lib'

  export default {
    mixins: [VueExtend.mixin],
    name: 'button-a',
    label: process.env.LABEL,
    style: process.env.STYLE,
    props: {
      text: {
        type: String,
        default: '提交',
        editor: {
          ignore: true
        },
      },
      url: {
        type: String,
        editor: {
          ignore: true
        }
      },
      color: {
        type: String,
        default: 'rgb(255, 255, 255)',
        editor: {
          ignore: true
        }
      },
      backgroundColor: {
        type: String,
        default: 'rgb(2, 181, 136)',
        editor: {
          ignore: true
        }
      },
      radius: {
        type: [String, Number],
        default: '3',
        editor: {
          ignore: true
        }
      },
      border: {
        type: String,
        default: '0',
        editor: {
          ignore: true
        }
      },
      borderColor: {
        type: [String, Number],
        editor: {
          ignore: true
        }
      }
    },
    computed: {
      ctext () {
        return this.scopeGet('text')
      },
      sty () {
        return {
          color: this.color,
          'background-color': this.backgroundColor,
          'border-radius': `${this.radius || 0}px`,
          'border-width': `${this.border || 0}px`,
          'border-color': this.borderColor
        }
      }
    },
    methods: {
      jump () {
        if (!this.url) return
        window.location.href = this.scopeGet('url')
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component {
    width: 100%
    height: 100%
    display: -webkit-box;
    -webkit-box-align: center;
    -webkit-box-pack: center;
    border-style: solid;
  }
</style>
