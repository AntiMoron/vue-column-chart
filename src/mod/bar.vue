<template>
  <div class="container">
    <div class="ii">
      <div class="inner">
        <div :style="blankStyle"></div>
        <div :style="barStyle"></div>
      </div>
      <p class="title">{{title}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "vue-column-chart-bar",
  props: ["value", "max", "color", "title"],
  computed: {
    upper: function() {
      if (this.max === 0) {
        return 200;
      }
      return this.max * 1.2;
    },
    division: function() {
      return 220000;
    },
    barFlex: function() {
      return Math.round(this.division * (this.value / this.upper));
    },
    barStyle: function() {
      return {
        flex: this.barFlex,
        backgroundColor: this.color,
        display: "flex",
        borderRadius: "15px",
        overflow: "hidden"
      };
    },
    blankStyle: function() {
      return {
        flex: this.division - this.barFlex,
        color: "transparent",
        display: "flex"
      };
    }
  }
};
</script>

<style scoped>
.container {
  width: 30px;
  overflow: hidden;
  justify-content: center;
  display: flex;
}

.ii {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.inner {
  width: 30px;
  border-radius: 15px;
  flex: 1;
  overflow: hidden;
  flex-direction: column;
  background-color: #ececec;
  display: flex;
}

.title {
  color: #999;
  font-weight: bold;
  font-size: 20px;
  align-self: flex-end;
}
</style>