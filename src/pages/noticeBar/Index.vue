<!--
 * @Author: weisheng
 * @Date: 2023-06-13 11:47:12
 * @LastEditTime: 2023-08-07 20:24:04
 * @LastEditors: weisheng
 * @Description:
 * @FilePath: \wot-design-uni\src\pages\noticeBar\Index.vue
 * 记得注释
-->
<template>
  <page-wraper>
    <demo-block title="基本用法">
      <wd-notice-bar text="这是一条消息提示信息这是一条消息提示信息这是一条消息提示信息" prefix="warn-bold" />
    </demo-block>

    <demo-block title="类型修改">
      <wd-notice-bar
        type="danger"
        text="当前网络不可用，请检查你的网络设置。当前网络不可用，请检查你的网络设置。"
        prefix="wifi-error"
        custom-class="space"
      />
      <wd-notice-bar
        type="info"
        text="pc-win沃特已登录，可在“设备管理”中查看详情。pc-win沃特已登录，可在“设备管理”中查看详情。"
        prefix="check-outline"
      />
    </demo-block>

    <demo-block title="禁止滚动">
      <wd-notice-bar :scrollable="false" text="通知被禁或时段内消息屏蔽可能造成消…" prefix="warn-bold"></wd-notice-bar>
    </demo-block>

    <demo-block title="插槽">
      <wd-notice-bar :scrollable="false">
        <template #prefix>
          <wd-icon custom-class="prefix" name="warn-bold">占位符</wd-icon>
        </template>
        通知被禁或时段内消息屏蔽可能造成消…
        <template #suffix>
          <div style="color: #4d80f0">查看</div>
        </template>
      </wd-notice-bar>
    </demo-block>

    <demo-block title="可关闭的">
      <wd-notice-bar text="挂起后，电脑与手机均不会有新客户接入。挂起后，电脑与手机均不会有新客户接入。" closable prefix="warn-bold" />
    </demo-block>

    <demo-block title="多行展示">
      <wd-notice-bar
        text="这是一条消息提示信息，这是一条消息提示信息，这是一条消息提示信息这是一条消息提示信息，这是一条消息提示信息，这是一条消息提示信息"
        wrapable
        :scrollable="false"
      />
    </demo-block>

    <demo-block title="自定义颜色">
      <wd-notice-bar
        text="这是一条消息提示信息，这是一条消息提示信息，这是一条消息提示信息"
        prefix="check-outline"
        color="#34D19D"
        background-color="#f0f9eb"
      ></wd-notice-bar>
    </demo-block>

    <demo-block title="多文本轮播">
      <wd-notice-bar :text="textArray" prefix="check-outline" @next="onNext" />
    </demo-block>

    <demo-block title="垂直滚动">
      <wd-notice-bar prefix="warn-bold" direction="vertical" :text="textArray" :speed="0.5" :delay="3" custom-class="space" />
      <wd-notice-bar prefix="warn-bold" direction="vertical" text="只有一条消息不会滚动" :speed="0.5" :delay="3" custom-class="space" />
      <wd-notice-bar prefix="warn-bold" direction="vertical" :text="textArray" :speed="0.5" :delay="3">
        <template #vertical="{ item, index }">
          <!-- 插槽内容不应该改变高度，例如设置height、padding等可能改变高度的样式，否则会导致滚动不准确 -->
          <view style="font-weight: 700; text-decoration: underline">{{ index }}: {{ item }}</view>
        </template>
      </wd-notice-bar>
    </demo-block>
  </page-wraper>
</template>
<script lang="ts" setup>
import { ref } from 'vue'

const textArray = ref([
  '欢迎使用wot design uni',
  '该组件库基于uniapp ->Vue3, ts构建',
  '项目地址：https://github.com/Moonofweisheng/wot-design-uni',
  '我们的目标是打造最强uniapp组件库',
  '诚挚邀请大家共同建设',
  '这是一条消息提示信息，这是一条消息提示信息，这是一条消息提示信息，这是一条消息提示信息，这是一条消息提示信息'
])

const onNext = (index: number) => {
  console.log('展示下一条，index: ', index)
  console.log('文本是：' + textArray.value[index])
}
</script>
<style lang="scss" scoped>
:deep(.prefix) {
  font-size: 18px;
  padding-right: 4px;
  width: 18px;
  height: 18px;
}

:deep(.space) {
  margin-bottom: 10px;
}
</style>
