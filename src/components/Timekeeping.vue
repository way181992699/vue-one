<template>
  <div class="Date">
    <div v-if="visible">还剩下{{m}}分:{{s}}秒关闭</div>
  </div>
</template>
<script>
export default {
  name: "Date",
  data() {
    return {
      d: "",
      h: "",
      m: "",
      s: "",
      visible: true,
      // endTime: 1800000,
      endTime: 70000,
      timeout: null,
      msg: ""
    };
  },
  created() {
    this.countTime();
  },
  destroyed() {
    clearInterval(this.countTime);
  },
  methods: {
    show() {
      this.visible = true;
    },
    countTime() {
      //时效为30分钟

      let endTime = this.endTime;
      if (endTime > 0) {
        this.m = Math.floor((endTime / 1000 / 60) % 60);
        this.s = Math.floor((endTime / 1000) % 60);
        this.endTime = endTime - 1000;
      } else {
        this.visible = false;
        this.$emit("close");
        return;
      }
      // console.log(this.m);

      //递归每秒调用countTime方法，显示动态时间效果
      this.timeout = setTimeout(this.countTime, 1000);
    }
  }
};
</script>