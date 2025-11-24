<template>
  <xz-vue-excel
    :src="excelSrc"
    :options="options"
    @rendered="renderedHandler"
    @error="errorHandler"
  />
</template>
<script lang="js" setup>
import { ref } from "vue";
import xzVueExcel from "../src/main.vue";
import '../src/index.css'

  // const excelSrc = ref("./pic.xlsx");
  // const excelSrc = ref("http://192.168.103.14:11090/ai-supremegpt/api/kb/file/download?file_id=a92fc354fdc6438890fe79a1c3945907");
  // const excelSrc = ref("./time.xls");
  // const excelSrc = ref("./time.xlsx");
  // const excelSrc = ref("./test.xlsx");
  const excelSrc = ref("./temp.xls");
  // const excelSrc = ref("./temp.xlsx");
  // const excelSrc = ref("./111.xlsx");
  // const excelSrc = ref("https://192.168.103.11:11090/ai-supremegpt/api/kb/file/download?file_id=5fae0f3dda994ab58ce4fd0981dd95f3");
  // const excelSrc = ref("./SpiritX-20250130.xlsx");
  // const excelSrc = ref("https://192.168.103.11:11090/ai-supremegpt/api/kb/file/download?file_id=db9f7e0c0ee5467eaff7d1439f4c9bf6");
  const options = ref({
    // mode: "read",
    // showContextmenu: true,
    // showBottomBar: false,
    // xls: true, // 预览xlsx文件设为false；预览xls文件设为true
    // xls: false, // 预览xlsx文件设为false；预览xls文件设为true
    xls: true, // 预览xlsx文件设为false；预览xls文件设为true
    minColLength: 0, // excel最少渲染多少列，如果想实现xlsx文件内容有几列，就渲染几列，可以将此值设置为0.
    minRowLength: 0, // excel最少渲染多少行，如果想实现根据xlsx实际函数渲染，可以将此值设置为0.
    widthOffset: 10, // 如果渲染出来的结果感觉单元格宽度不够，可以在默认渲染的列表宽度上再加 Npx宽
    heightOffset: 10, // 在默认渲染的列表高度上再加 Npx高
    beforeTransformData: (workbookData) => {
      console.log("beforeTransformData workbookData====", workbookData);

      return workbookData;
    }, // 底层通过exceljs获取excel文件内容，通过该钩子函数，可以对获取的excel文件内容进行修改，比如某个单元格的数据显示不正确，可以在此自行修改每个单元格的value值。
    transformData: (workbookData) => {
      console.log("transformData workbookData====", workbookData);
      return workbookData;
    } // 将获取到的excel数据进行处理之后且渲染到页面之前，可通过transformData对即将渲染的数据及样式进行修改，此时每个单元格的text值就是即将渲染到页面上的内容
  });
  const renderedHandler = () => {
    console.log("渲染完成");
  };
  const errorHandler = () => {
    console.log("渲染失败");
  };
</script>
