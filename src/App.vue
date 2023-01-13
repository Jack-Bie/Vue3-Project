<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ElConfigProvider } from "element-plus"
import zhCn from "element-plus/lib/locale/lang/zh-cn"
</script>

<template>
   <div>
    <el-config-provider :locale="zhCn">
      <RouterLink to="/"></RouterLink>
      <RouterView />
    </el-config-provider>
  </div>
</template>

<style scoped>

</style>
