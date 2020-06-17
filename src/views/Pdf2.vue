<template>
  <div>
    <p class="arrow">
      <span @click="changePdfPage(0)" class="turn">Preview</span>
      {{currentPage}} / {{pageCount}}
      <span @click="changePdfPage(1)" class="turn">Next</span>
    </p>
    <v-pdf
      :page="currentPage"
      @num-pages="pageCount=$event"
      @page-loaded="currentPage=$event"
      @loaded="loadPdfHandler"
      src="http://file.dakawengu.com/file/2018-05-29/20180527-tianfeng.pdf"
    ></v-pdf>
  </div>
</template>

<script>
import pdf from "vue-pdf";

export default {
  data() {
    return {
      currentPage: 0, // pdf文件页码
      pageCount: 0, // pdf文件总页数
      fileType: "pdf", // 文件类型
      src: "" // pdf文件地址
    };
  },
  created() {
    // 有时PDF文件地址会出现跨域的情况,这里最好处理一下
    // this.src = pdf.createLoadingTask(this.src);
  },
  components: {
    "v-pdf": pdf
  },
  methods: {
    changePdfPage(val) {
      // console.log(val)
      if (val === 0 && this.currentPage > 1) {
        this.currentPage--;
      }
      if (val === 1 && this.currentPage < this.pageCount) {
        this.currentPage++;
      }
    },
    loadPdfHandler() {
      this.currentPage = 1; // 加载的时候先加载第一页
    }
  }
};
</script>
