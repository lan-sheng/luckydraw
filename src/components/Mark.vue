<template>
  <div>
    <div class="mask" v-if="showToast"></div>
    <div class="lottery-alert" v-if="showToast">
      <h1>恭喜您</h1>
      <p>
        <img :src="list[index].img" alt />
      </p>
      <h2>获得{{list[index].title}}</h2>
      <div class="btnsave" @click="showToast=false">确定</div>
    </div>
  </div>
</template>

<script>
import bus from "../bus";
export default {
  data() {
    return {
      showToast: false, //显示弹出弹层
      index: -1 //开始下标
    };
  },
  props: ["list"],
  created() {
    bus.$on("showToast", (bool, i) => {
      window.console.log("index: ", i);
      this.showToast = bool;
      this.index = i;
    });
  }
};
</script>

<style>
.mask {
  height: 100%;
  width: 100%;
  background: rgba(0, 0, 0, 0.6);
  position: fixed;
  top: 0;
  left: 0;
}
.lottery-alert {
  width: 400px;
  height: 200px;
  background: #fff;
  border-radius: 15px;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  margin: auto;
  z-index: 10;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.lottery-alert img {
  width: 40px;
  height: 40px;
}
.btnsave {
  margin-top: 20px;
  font-size: 24px;
}
</style>