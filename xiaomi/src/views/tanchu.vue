<template>
 
<div class="storeList">
 
<transition name="fade">
 
<div class="imgMask" v-if="showBigImg" @click.stop="showBigImg=!showBigImg">
 
      <img class="prev" @click.stop="prev" src="@/assets/img/left.png">
 
      <div class="showImg">
 
        <img class="bigImg" :src="imgList[num]">
 
      </div>
 
      <img class="next" @click.stop="next" src="@/assets/img/right.png">
 
    </div>
 
</transition>
 
<div class="imgbox">
 
<img v-for="(item,index) in imgList" :key="index" @click="bigImg(index)" :src="item" alt="" />
 
</div>
 
</div>
 
</template>
 
 
 
<script>
 
export default {
 
data() {
 
return {
 
showBigImg: false,
 
num: 0,
 
imgList: [
 
"http://boweisou.oss-cn-shenzhen.aliyuncs.com/images/10412/2018/07/hv18kDRs2rp51501opsRmsoMQopo11.jpg",
 
"https://img.alicdn.com/imgextra/i4/0/TB2Gu..FL9TBuNjy1zbXXXpepXa_!!0-rate.jpg_400x400.jpg",
 
"https://g-search3.alicdn.com/img/bao/uploaded/i4/i2/2846819868/TB2G0p0fGQoBKNjSZJnXXaw9VXa_!!2846819868.jpg_230x230.jpg",
 
"http://boweisou.oss-cn-shenzhen.aliyuncs.com/images/10412/2018/07/N5Mlj4LN4dA444LI9bx8n8bMdJZA5m.jpg",
 
"http://boweisou.oss-cn-shenzhen.aliyuncs.com/images/10412/2018/07/kbR4RhTd4H0BAv48EBpdRBVBpbAa08.jpg"
 
]
 
};
 
},
 
methods: {
 
bigImg(index) {
 
this.showBigImg = true;
 
this.num = index;
 
},
 
prev() {
 
if (this.num == 0) {
 
this.num = this.imgList.length;
 
}
 
this.num--;
 
},
 
next() {
 
if (this.num == this.imgList.length - 1) {
 
this.num = -1;
 
}
 
this.num++;
 
}
 
}
 
};
 
</script>
 
<style lang="less" scoped>
 
.storeList {
 
width: 100%;
 
.imgbox {
 
width: 80%;
 
margin: 300px 8%;
 
display: flex;
 
justify-content: flex-start;
 
align-items: center;
 
flex-wrap: wrap;
 
img {
 
width: 150px;
 
height: 150px;
 
margin-right: 5px;
 
object-fit: cover;
 
cursor: pointer;
 
}
 
}
 
.imgMask {
 
position: fixed;
 
height: 100%;
 
width: 100%;
 
top: 0;
 
left: 0;
 
z-index: 100;
 
background: rgba(0, 0, 0, 0.6);
 
.showImg {
 
height: auto;
 
width: auto;
 
position: absolute;
 
left: 50%;
 
top: 50%;
 
transform: translate(-50%, -50%);
 
border: 10px solid #fff;
 
img {
 
width: 100%;
 
height: 100%;
 
}
 
}
 
.prev {
 
position: absolute;
 
top: 50%;
 
left: 10px;
 
width: 40px;
 
transform: translate(10px, -50%);
 
cursor: pointer;
 
}
 
.next {
 
width: 40px;
 
transform: translate(10px, -50%);
 
position: absolute;
 
top: 50%;
 
right: 20px;
 
cursor: pointer;
 
}
 
}
 
}
 
　.fade-enter-active,
 
.fade-leave-active {
 
transition: all 0.2s linear;
 
transform: translate3D(0, 0, 0);
 
}
 
　.fade-enter,
 
.fade-leave-active {
 
transform: translate3D(100%, 0, 0);
 
}