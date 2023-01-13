<script setup>
import { ref } from "vue";
import {tableData} from '../mock'
</script>

<template>
  <div class="container">

    <el-select v-model="selectedValue" placeholder="请选择类型" clearable="">
      <el-option label="new_channel" value="new_type"></el-option>
      <el-option label="old_channel" value="old_type"></el-option>
    </el-select>

    <el-table :data="tableData" :border="true" style="width: 100%" stripe :fit="true">
      <el-table-column type="selection" width="55" />
      <el-table-column prop="tag_name" label="名称" width="150" />
      <el-table-column prop="tag_id" label="Tag ID" width="150" />
      <el-table-column prop="tag_type" label="类型" width="150" />
      <el-table-column prop="subscribed_count" label="订阅数" width="100" />
      <el-table-column prop="archive_count" label="投稿数" width="100" />
      <el-table-column prop="type" label="类型" width="100" />
      <el-table-column prop="short_content" label="简述" width="180" show-overflow-tooltip />
      <el-table-column prop="content" label="详述" width="180" show-overflow-tooltip />
    </el-table>

    <el-pagination
      v-model:current-page="currentPage"
      v-model:page-size="pageSize"
      :page-sizes="[10, 15, 20, 25,30]"
      :default-page-size = "10"
      :default-current-page = "1"
      :small="small"
      :disabled="disabled"
      :background="background"
      layout="total, sizes, prev, pager, next"
      :total="81"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
    />
  </div>
</template>

<script>
const selectedValue = ref("")
</script>

<style scoped>
.container{
  width: 100%;
}
</style>