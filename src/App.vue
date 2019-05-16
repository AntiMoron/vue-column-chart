<template>
  <div class="chart">
    <chart :items="items"/>
  </div>
</template>

<script>
import Chart from "./Chart";

export default {
  components: { Chart },
  data: function() {
    const items = [];
    for (let i = 0; i < 30; i++) {
      items.push({
        value: i,
        color: "red",
        title: "第" + i + "天"
      });
    }
    return {
      items
    };
  }
};
</script>

<style scoped>
.chart {
  width: 2500px;
}
</style>
