<template>
  <div class="lucky-draw">
    <div class="lucky-draw-list">
      <div class="button-start">
        <div class="box" @click="rollStart">
          <p>
            <b>抽奖</b>
          </p>
        </div>
      </div>
      <ul class="product">
        <li v-for="(item, i) in list" :key="i" :class="i === index ? 'on' : ''">
          <div class="boxs">
            <img class="img" :src="item.img" alt />
            <p>{{ item.title }}</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import bus from "../bus";
export default {
  props: ["list"],
  data() {
    return {
      showToast: false, //显示弹出弹层
      index: -1, //开始下标
      prize: -1, //奖品位置
      speed: 200, //滚动速度
      cycle: 50, //要求走动次数
      times: 0, //走动次数
      timer: null //定时器
    };
  },
  methods: {
    rollStart() {
      this.rollRun();
    },
    rollRun() {
      this.times++;
      this.rollBtn();
      window.console.log(this.times, this.cycle + 10, this.index, this.prize);
      if (this.index == this.prize && this.times >= this.cycle + 10) {
        clearTimeout(this.timer);
        this.times;
        this.speed = 200;
        this.prize = -1;
        setTimeout(() => {
          bus.$emit("showToast", true, this.index);
          // this.showToast = true;
        }, 300);
      } else {
        if (this.times < this.cycle) {
          this.speed -= 20;
        } else if (this.times == this.cycle) {
          //生成中奖位置
          this.prize = Math.floor(Math.random() * 8);
        } else if (this.times > this.cycle + 10) {
          this.speed += 110;
        } else {
          this.speed += 40;
        }
        if (this.speed <= 40) {
          this.speed = 40;
        }
        this.timer = setTimeout(this.rollRun, this.speed);
      }
    },
    rollBtn() {
      let index = this.index;
      this.index = index++ > 6 ? 0 : index;
    }
  }
};
</script>

<style>
</style>