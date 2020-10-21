<template>
  <div class="about">
    <h1>This is an about page</h1>
    <el-divider>
      <i class="el-icon-mobile-phone"></i>
    </el-divider>
    <el-tabs tab-position="left" class="tab-css">
      <el-tab-pane label="小工具">
        <el-row>
          <el-col :span="6">
            <el-card class="box-card" shadow="hover">
              <div slot="header" class="clearfix">
                <span>计时器</span>
                <el-button
                  style="float: right; padding: 3px 0"
                  type="text"
                  @click="clickTime"
                >{{demo}}</el-button>
              </div>
              <div v-if="close">
                <time-keep ref="TimeKeep" @close="closeTime"></time-keep>
              </div>
            </el-card>
          </el-col>
          <el-col :span="6"></el-col>
          <el-col :span="6"></el-col>
        </el-row>
      </el-tab-pane>
      <el-tab-pane label="小案例">
        <el-row>
          <el-col :span="6">
            <el-card>
              <div slot="header" class="clearfix">
                <span>插槽案例</span>
                <el-button
                  type="text"
                  style="float: right; padding: 3px 0"
                  @click="clickSlot"
                >{{demo}}</el-button>
              </div>
              <slot-use></slot-use>
              <el-divider>
                <i class="el-icon-picture"></i>
              </el-divider>
              <div>
                <el-image
                  :src="require('@/assets/slot/slot00.png')"
                  fit="cover"
                  :preview-src-list="[require('@/assets/slot/slot00.png')]"
                ></el-image>
                <!-- <img style="width: 100px; height: 100px" src="../assets/slot/slot00.png" /> -->
              </div>
            </el-card>
          </el-col>
          <el-col :span="6"></el-col>
          <el-col :span="6"></el-col>
        </el-row>
      </el-tab-pane>
      <el-tab-pane label="小知识">小知识</el-tab-pane>
      <el-tab-pane label="其他">其他</el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import TimeKeep from "@/components/Timekeeping.vue";
import SlotUse from "@/components/slot/slot.vue";
export default {
  components: {
    TimeKeep,
    SlotUse
  },
  data() {
    return {
      close: false,
      fits: "fill",
      url:
        "https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg",
      srcList: [
        "http://192.168.1.21:8080/src/assets/slot/slot00.png",
        "https://fuss10.elemecdn.com/1/8e/aeffeb4de74e2fde4bd74fc7b4486jpeg.jpeg"
      ]
    };
  },
  computed: {
    demo: {
      get() {
        return this.close ? "关闭" : "演示";
      }
    }
  },
  methods: {
    clickTime() {
      if (!this.close) {
        this.close = true;
        this.$refs.TimeKeep.show();
      } else {
        this.close = false;
      }
    },
    clickSlot() {
      if (!this.close) {
        this.close = true;
        // this.$refs.TimeKeep.show();
      } else {
        this.close = false;
      }
    },
    closeTime() {
      this.close = false;
    }
  }
};
</script>

<style >
.text {
  font-size: 14px;
}

.item {
  margin-bottom: 18px;
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}
.clearfix:after {
  clear: both;
}

.box-card {
  min-height: 300px;
}
.tab-css {
  min-height: 200px;
}
.about {
  height: 600px;
}
</style>