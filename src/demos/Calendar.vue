<template>
  <div>
    <group>
      <calendar v-model="demo1" :title="$t('Basic Usage')" disable-past placeholder="placeholder" @on-show="log('show')" @on-hide="log('hide')"></calendar>
    </group>

    <group>
      <calendar v-model="demo2" :title="$t('Set value as TODAY')" disable-past></calendar>
    </group>

    <group>
      <calendar @on-change="onChange" v-model="demo3" :title="$t('Disable future')" disable-future></calendar>
    </group>

    <group>
      <calendar @on-change="onChange" v-model="demo4" :title="$t('Show popup header')" show-popup-header :popup-header-title="$t('Please select')" disable-future></calendar>
    </group>

    <group>
      <calendar placeholder="placeholder" @on-change="onChange" v-model="demo5" :title="$t('Multiple dates')" :popup-header-title="$t('Please select')" disable-future></calendar>
    </group>

     <group>
      <calendar :display-format="displayFormat" :placeholder="$t('Please select')" @on-change="onChange" v-model="demo6" :title="$t('Format multiple dates')" :popup-header-title="$t('please select')" disable-future></calendar>
      <cell-box align-items="flex-start">
        <span class="selected-days">value:</span>
        <div>
          <badge v-for="day in demo6" :text="day" :key="day" style="margin-right:10px;"></badge>
        </div>
      </cell-box>
    </group>
  </div>
</template>

<i18n>
Basic Usage:
  zh-CN: 一般使用
Set value as TODAY:
  zh-CN: 设置时间为今天
Disable future:
  zh-CN: 禁止选择未来时间
Show popup header:
  zh-CN: 显示 popup 头部
Please select:
  zh-CN: 请选择日期
Multiple dates:
  zh-CN: 多选
Format multiple dates:
  zh-CN: 格式化表单值
</i18n>

<script>
import { Group, Calendar, Cell, Badge, CellBox } from 'vux'

export default {
  components: {
    Calendar,
    Group,
    Cell,
    Badge,
    CellBox
  },
  data () {
    return {
      demo1: '',
      demo2: 'TODAY',
      demo3: 'TODAY',
      demo4: 'TODAY',
      demo5: [],
      demo6: [],
      displayFormat (value, type) {
        if (type === 'string') {
          return value
        } else {
          return value.length ? (value.length + ' days') : ''
        }
      }
    }
  },
  methods: {
    log (str) {
      console.log(str)
    },
    onChange (val) {
      console.log('on change', val)
    }
  }
}
</script>

<style scoped>
.selected-days {
  color: #999;
  width: 90px;
}
</style>
