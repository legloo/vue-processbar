# vue-processbar
 ```
 npm i vue-processbar -S
 ```

# Usage
```js
1.import vueProcessbar from 'vue-processbar'

2.components: {
    vueProcessbar
  }
3.options:{//default props
    height:'30px',//进度条高度
    radius:'15px',//进度条圆角 可为px、%等
    time:'3000ms',//动画开始到结束时间
    animate:'ease-in-out',//动画效果
    progress:50,//最终进度
    barColor:['red','blue'],//渐变色区
    showZebra:true//是否显示斑马纹
}
      
4.   <vueProcessbar :options="options" />


```
