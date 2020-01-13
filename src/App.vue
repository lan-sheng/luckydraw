
<template>
  <div id="app">
    <Title />
    <LuckyDrawList :list="list" />
    <Mark :list="list" />
  </div>
</template>

<script>
import LuckyDrawList from "./components/LuckyDrawList.vue";
import Title from "./components/Title.vue";
import Mark from "./components/Mark.vue";

export default {
  components: {
    LuckyDrawList,
    Title,
    Mark
  },
  data() {
    return {
      list: [
        { img: require("./assets/j1.png"), title: "谢谢参与" },
        { img: require("./assets/j2.png"), title: "美女一个" },
        { img: require("./assets/j1.png"), title: "宝马一辆" },
        { img: require("./assets/j2.png"), title: "单车一辆" },
        { img: require("./assets/j1.png"), title: "鸡蛋一蓝" },
        { img: require("./assets/j2.png"), title: "500红包" },
        { img: require("./assets/j1.png"), title: "靓号一个" },
        { img: require("./assets/j2.png"), title: "鲜花一蓝" }
      ]
    };
  }
};
</script>
// 样式
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: radial-gradient(49% 160%, #22b5ff 0, #3a72fa 100%);
  font-size: 14px;
  height: 100%;
}
ul li {
  list-style: none;
}

#app {
  overflow: hidden;
}
.lucky-draw {
  animation: changebg 0.5s ease infinite;
  overflow: hidden;
  padding: 20px;
  width: 400px;
  margin: 0 auto;
  background-repeat: no-repeat;
  background-size: 100% 100%;
}
@keyframes changebg {
  0% {
    background-image: url(./assets/k1.png);
  }
  100% {
    background-image: url(./assets/k2.png);
  }
}
.lucky-draw-list {
  height: 340px;
  position: relative;
  margin-top: 10px;
  margin-left: 10px;
}
.button-start {
  position: absolute;
  left: 33.33333333%;
  width: 33.3333333%;
  top: 110px;
  padding-right: 10px;
}
.box {
  height: 100px;
  font-size: 40px;
  text-align: center;
  line-height: 100px;
  color: #fff;
  overflow: hidden;
  background: url(./assets/bg1.png) no-repeat center;
  background-size: 100% 100%;
}
.product li {
  height: 100px;
  text-align: center;
  overflow: hidden;
  background: url(./assets/bg2.png) no-repeat center;
  background-size: 100% 100%;
  width: 30.333333%;
  position: absolute;
}
.product li:nth-child(2) {
  left: 33.3333333%;
}
.product li:nth-child(3) {
  left: 66.6666666%;
}
.product li:nth-child(4) {
  left: 66.6666666%;
  top: 110px;
}
.product li:nth-child(5) {
  left: 66.6666666%;
  top: 220px;
}
.product li:nth-child(6) {
  left: 33.3333333%;
  top: 220px;
}
.product li:nth-child(7) {
  left: 0;
  top: 220px;
}
.product li:nth-child(8) {
  left: 0;
  top: 110px;
}
.img {
  display: block;
  height: 50px;
  margin: 0 auto;
  margin-top: 10px;
  margin-bottom: 5px;
}
.product li.on {
  background: url(./assets/bg1.png) no-repeat center;
  background-size: 100% 100%;
}
.title2 {
  color: #fff;
  font-size: 18px;
  padding: 50px 0;
  text-align: center;
}
</style>
