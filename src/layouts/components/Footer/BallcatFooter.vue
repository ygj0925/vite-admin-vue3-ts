<template>
  <footer-view :footer-style="{ margin: '16px 0' }">
    <template #links>
      <a href="https://ant.design/" rel="noreferrer">Ant Design</a>
      <a href="https://antdv.com/" rel="noreferrer">Ant Design Vue</a>
    </template>
    <template #copyright>
      Copyright <copyright-outlined /> 2022 <span>🐱 Antd Pro 组织出品</span>
    </template>
  </footer-view>
</template>

<script setup lang="ts">
import FooterView from '#/layout/Footer'
</script>
