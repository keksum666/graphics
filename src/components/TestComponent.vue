<template>
  <div>
    <VueForceGraphVR :graphData="graphData" backgroundColor="#090723" style="height: 800px"></VueForceGraphVR>
  </div>
</template>

<script>

import axios from 'axios';
import { VueForceGraphVR } from "vue-force-graph/es/components/vue-force-graph-vr";

export default {
  name: "TestComponent",
  components: {
    VueForceGraphVR,
  },
  data: () => ({
    graphData: {
      "nodes": [
      ],
      "links": [
      ]
    }
  }),
  async created(){
    await axios.get('http://localhost:8000/api/module/articles/graph-data').then((response) => {
      this.graphData = response.data;
    })
  }
}
</script>

<style scoped>
.graph-nav-info {
  height: 800px !important;
}
</style>