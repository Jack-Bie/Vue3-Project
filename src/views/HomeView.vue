<script setup>
import { ref } from "vue";
import {TableData} from '../mock'
</script>

<template>
  <div class="container">
    <!-- 选择器 -->
    <el-select 
      v-model="selectedValue" 
      placeholder="请选择类型" 
      clearable
      @change="getSecletedValue"
    >
      <el-option label="new_channel" value="new_channel"></el-option>
      <el-option label="old_channel" value="old_channel"></el-option>
    </el-select>

    <!-- 表格 -->
    <el-table 
      :data="Data.slice(pageSize*(currentPage-1),pageSize*currentPage)" 
      :border="true" 
      :row-key="getRowKey" 
      style="width: 100%" 
      stripe 
    >
      <el-table-column type="selection" width="55" :reserve-selection="true" />
      <el-table-column 
        v-for="(item,index) in tableHeader" 
        :key="index" 
        :prop="index" 
        :label="item[0]" 
        :width="item[1]" 
        show-overflow-tooltip 
      />
    </el-table>

    <!-- 分页器 -->
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
//定义部分用到的数据，mock.js文件进行了适当的修改
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
let Data = TableData("")

//实现数据分页
let total = Data.length
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

//选择器实现数据过滤
const getSecletedValue = (val) =>{
  Data = TableData(val)
  total = Data.length
}

//解决翻页后选中消失问题
//需要给el-table加上row-key属性
//需要给el-table-column加上:reserve-selection="true"属性
const getRowKey = (row) => row.tag_id

</script>

<style scoped>
.container{
  width: 100%;
}
</style>