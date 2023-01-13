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

    <el-table :data="tableData.slice(pageSize*(currentPage-1),pageSize*currentPage)" :border="true" style="width: 100%" stripe >
      <el-table-column type="selection" width="55" />
      <el-table-column v-for="(item,index) in tableHeader" :key="index" 
        :prop="index" :label="item[0]" :width="item[1]" show-overflow-tooltip />
    </el-table>

    <el-pagination
      v-model:current-page="currentPage"
      v-model:page-size="pageSize"
      :page-sizes="[10, 15, 20, 25,30]"
      background
      layout="total, sizes, prev, pager, next"
      :total="total"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
    />
  </div>
</template>

<script>
const selectedValue = ref("")
const tableHeader = {
  tag_name:["名称",150],
  tag_id:["Tag ID",150],
  tag_type:["类型",150],
  subscribed_count:["订阅数",100],
  archive_count:["投稿数",100],
  type:["类型",100],
  short_content:["简述",180],
  content:["详述",180],
}

//分页数据
const total = tableData.length
let pageSize = ref(10)
let currentPage = ref(1)
//调节pageSize后使当前页面回到第1页
const handleSizeChange = (val) => {
  pageSize = ref(val)
  currentPage = ref(1)
}
const handleCurrentChange = (val) => {
  currentPage = ref(val)
}
</script>

<style scoped>
.container{
  width: 100%;
}
</style>