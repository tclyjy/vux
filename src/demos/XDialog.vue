<template>
  <div style="height: 1000px">
    <group>
      <x-switch v-model="show" :title="$t('Toggle')"></x-switch>
      <x-switch v-model="showHideOnBlur" :title="$t('hide on clicking mask')"></x-switch>
    </group>
    <group style="padding-top: 300px">
      <x-switch v-model="showNoScroll" :title="$t('disable background scrolling')"></x-switch>
    </group>
    <div v-transfer-dom>
      <x-dialog v-model="show" class="dialog-demo">
        <div class="img-box">
          <img src="../assets/demo/dialog/01.jpg" style="max-width:100%">
        </div>
        <div @click="show=false">
          <span class="vux-close"></span>
        </div>
      </x-dialog>
    </div>
    <div v-transfer-dom>
      <x-dialog v-model="showHideOnBlur" class="dialog-demo" :hideOnBlur="true">
        <div class="img-box">
          <img src="../assets/demo/dialog/01.jpg" style="max-width:100%">
        </div>
        <div @click="showHideOnBlur=false">
          <span class="vux-close"></span>
        </div>
      </x-dialog>
    </div>
    <div v-transfer-dom>
      <x-dialog v-model="showNoScroll" class="dialog-demo" :scroll="false">
        <div class="img-box">
          <img src="../assets/demo/dialog/01.jpg" style="max-width:100%">
        </div>
        <div @click="showNoScroll=false">
          <span class="vux-close"></span>
        </div>
      </x-dialog>
    </div>

    <group style="padding-top: 300px">
      <x-switch v-model="showScrollBox" :title="$t('long long content')"></x-switch>
    </group>
    <div v-transfer-dom>
      <x-dialog v-model="showScrollBox" class="dialog-demo">
        <p class="dialog-title">Long content</p>
        <div class="img-box" style="height:100px;padding:15px 0;overflow:scroll;-webkit-overflow-scrolling:touch;">
          <p v-for="i in 20">{{i}}</p>
        </div>
        <div @click="showScrollBox=false">
          <span class="vux-close"></span>
        </div>
      </x-dialog>
    </div>

  </div>
</template>

<i18n>
hide on clicking mask:
  zh-CN: 点击遮罩自动关闭
Toggle:
  zh-CN: 显示/隐藏
disable background scrolling:
  zh-CN: 背景不可滚动
long long content:
  zh-CN: 很长很长的内容
</i18n>

<script>
import { XDialog, XButton, Group, XSwitch, TransferDomDirective as TransferDom } from 'vux'

export default {
  directives: {
    TransferDom
  },
  components: {
    XDialog,
    XButton,
    Group,
    XSwitch
  },
  data () {
    return {
      show: false,
      showNoScroll: false,
      showHideOnBlur: false,
      showScrollBox: false
    }
  }
}
</script>

<style lang="less" scoped>
@import '~vux/src/styles/close';

.dialog-demo {
  .weui-dialog{
    border-radius: 8px;
    padding-bottom: 8px;
  }
  .dialog-title {
    line-height: 30px;
    color: #666;
  }
  .img-box {
    height: 350px;
    overflow: hidden;
  }
  .vux-close {
    margin-top: 8px;
    margin-bottom: 8px;
  }
}
</style>
