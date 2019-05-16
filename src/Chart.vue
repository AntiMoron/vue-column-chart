<template>
  <div class="container">
    <bar
      class="bar"
      v-for="(item, index) in items"
      :value="item.value"
      :color="item.color"
      :max="maxValue"
      :key="index"
      :title="item.title"
    />
  </div>
</template>

<script>
import Bar from "./mod/bar";
export default {
  name: "vue-column-chart",
  components: { Bar },
  props: ["items"],
  computed: {
    maxValue: function() {
      console.log(
        (this.items || []).reduce((pre, cur) => {
          return Math.max(cur.value || 0, pre);
        }, 0)
      );
      return (this.items || []).reduce((pre, cur) => {
        return Math.max(cur.value || 0, pre);
      }, 0);
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  height: 300px;
  flex-direction: row;
  width: 100%;
  justify-content: space-between;
}
.bar {
  display: flex;
  flex: 1;
}
</style>
