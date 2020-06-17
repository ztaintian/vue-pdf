<template>
  <div>
    <v-pdf src="/static/test.pdf"></v-pdf>
    <!-- <iframe href="../../static/test.pdf"></iframe> -->
  </div>
</template>

<script>
import pdf from "vue-pdf";

export default {
  name: "pdf",
  components: {
    'v-pdf': pdf
  }
};
</script>
