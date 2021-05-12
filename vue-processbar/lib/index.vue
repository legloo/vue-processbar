<template>
    <div class="bar-container" :style="fbarStyle">
      <div class="bar" :style="cbarStyle" >
        <div class="bar-back" v-if="showZebra"></div>
      </div>
    </div>
</template>

<script>
export default {
  name: "vue-processbar",
  data() {
    return {
      left:'-100%',
    };
  },
  props: {
    options: {
      type: Object,
      default: function () {
        return {
         height:'30px',//进度条高度
         radius:'15px',//进度条圆角 可为px、%等
         time:'300ms',//动画开始到结束时间
         animate:'ease-in-out',//动画效果
         progress:50,//最终进度
         barColor:['red','blue'],//渐变色区
         showZebra:true//是否显示斑马纹
        };
      },
    },
  },
  computed:{
      fbarStyle(){
          return{
              height:this.options.height,
              borderRadius:this.options.radius
          }
      },
      cbarStyle(){
          return {
              backgroundImage:`linear-gradient(to right, ${this.options.barColor[0]}, ${this.options.barColor[1]})`,
              transition: `all ${this.options.time} ${this.options.animate}`,
              left:this.left
          }
      },
      showZebra(){
          return this.options.showZebra
      }
  },
  mounted() {
    setTimeout(() => {
      this.left =  -100+this.options.progress+'%';
    });
  },
  filters: {},
  methods: {},
};
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.bar-container {
  position: relative;
  background-color: #fff;
  width: 100%;
  height: 30px;
  border-radius: 20px;
  overflow: hidden;
  .bar {
    // background-image: linear-gradient(to right, red, blue);
    width: 100%;
    height: 100%;
    position: absolute;
    left: -100%;
    // transition: all 800ms ease-in-out;
    .bar-back {
      background-image: linear-gradient(90deg, transparent 50%, #fff 10%);
      background-size: 5px 10%;
      width: 100%;
      height: 100%;
      position: absolute;
      left: 0px;
    }
  }
}
</style>
