<script setup lang="ts">
import "ag-grid-community/dist/styles/ag-grid.css";
import "ag-grid-community/dist/styles/ag-theme-alpine.css";
import { AgGridVue } from 'ag-grid-vue3';
import type {ColDef} from "ag-grid-community";
import personFilter from "@/personFilter.vue";
import HeaderRender from "@/HeaderRender.vue";



const rowData: { name: string; age: number; grade: number; enGrade: number }[] = [
  { name: '张三', age: 19, grade: 70, enGrade: 78 },
  { name: '李四', age: 18, grade: 80, enGrade: 80 },
  { name: '王五', age: 20, grade: 100, enGrade: 79 },
];

const gridOptions = {
  animateRows: true, // 行动画，体现在排序时的动画等
  suppressCellSelection: true, // suppressCellFocus关闭键盘导航，可以移除鼠标点击focus时的焦点
  context: {
  },
};
const customFrameWorkComponents = {
  personFilter: personFilter,
  headerRenderComponent: HeaderRender,
};

const columnDefs: ColDef[] = [
  {
    field: 'name',
    headerName: '姓名',
    resizable: true,
    filter: 'personFilter', // https://www.ag-grid.com/archive/26.0.0/angular-data-grid/component-filter/
    headerComponent: 'headerRenderComponent', // 表头容器组件
    sortable: false,
  },
  {
    field: 'age',
    headerName: '年龄',
    filter: 'personFilter',

    resizable: true,
    sortable: true,
  },
  {
    field: 'enGrade',
    headerName: '英文成绩',
    filter: 'filterRenderComponent',

    resizable: true,
    sortable: true,
  },
  {
    field: 'grade',
    headerName: '成绩',

    filter: 'filterRenderComponent',
    resizable: true,
    sortable: true,
  },
];
</script>

<template>
  <ag-grid-vue
      style="width: 500px; height: 200px"
      :always-show-vertical-scroll="true"
      :framework-components="customFrameWorkComponents"
      :header-height="32"
      class="ag-theme-alpine"
      :grid-options="gridOptions"
      :column-defs="columnDefs"
      :row-data="rowData"
  >
  </ag-grid-vue>
</template>

<style scoped>


</style>
