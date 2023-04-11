<template>
  <div class="center">
    <div class="center-top">
      <div>
        <div :style="{color:'#009DB9',fontSize:'16px'}">累计营养液(T)</div>
        <div :style="{color:'#0FE5F0 ',fontSize:'30px','text-align':'center'}">202</div>
      </div>
      <div>
        <div :style="{color:'#009DB9',fontSize:'16px'}">累计耗电量(W)</div>
        <div :style="{color:'#0FE5F0 ',fontSize:'30px','text-align':'center'}">159357</div>
      </div>
      <div>
        <div :style="{color:'#009DB9',fontSize:'16px'}">累计产量(吨)</div>
        <div :style="{color:'#0FE5F0 ',fontSize:'30px','text-align':'center'}">159357</div>
      </div>
    </div>
    <div class="center-center"></div>
    <div class="center-bottom">
      <div class="center-bottom-left">
        <div> 大棚数量:<span>32</span></div>
        <div> 种植面积: <span>300㎡</span></div>
        <div> 灌水量: <span>1000T</span></div>
        <div> 耗电量: <span>300W</span></div>
      </div>
      <div class="center-bottom-center">
        <div class="landingale" ></div>
      </div>

      <div class="center-bottom-right">
        <ul>
          <li> 空心菜<span>6726株</span></li>
          <li> 生菜 <span>2597株</span></li>
          <li> 叶甜菜 <span>2000株</span></li>
          <li> 木耳菜 <span>936株</span></li>
        </ul>

      </div>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts';
import { onMounted, reactive, ref, toRefs } from "vue";
export default {
  setup (props, context) {
    let state = reactive({})
    onMounted(() => {
      setTimeout(() => { initEcharts(); }, 500)
    })
    const initEcharts = () => {
      const myechart = echarts.init(document.querySelector('.landingale'));
      myechart.setOption({
        tooltip: {
         show : false,
          trigger: 'item'
        },
        legend: {
          show: false,
        },
        series: [
          {
            type: 'pie',
            radius: ['40%', '70%'],
            avoidLabelOverlap: false,
            itemStyle: {
              emphasis: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              },
              normal: {
                label: {
                  fontSize: '15',
                  show: true,
                  formatter: '{b} : {c} ({d}%)' ,//带当前图例名 + 百分比
                },
                labelLine: { show: true },
               
              },

             
            },
            label: {
              show: false,
              position: 'center'
            },
            emphasis: {
              label: {
                show: true,
                fontSize: '15',
                fontWeight: 'bold'
              }
            },
            labelLine: {
              show: false
            },



            data: [
              { value: 6726, name: '空心菜' },
              { value: 735, name: '生菜' },
              { value: 580, name: '叶甜菜' },
              { value: 600, name: '木耳菜' },

            ]
          }
        ]
      })

    }

    return {
      initEcharts,
      ...toRefs(state)
    }
  }
}
</script>

<style lang="less" scoped>
.center {
  width: 100%;
  height: 100%;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  &-top {
    display: flex;
    margin-top: 20px;
    width: 100%;
    height: 120px;
    border: 2px solid #106875;
    box-sizing: border-box;

    justify-content: space-around;
    align-items: center;
  }
  &-center {
    margin-top: 20px;
    flex: 1;
    border: 2px solid #106875;
    box-sizing: border-box;
  }
  &-bottom {
    margin-top: 20px;
    width: 100%;
    height: 257px;

    border: 2px solid #106875;
    box-sizing: border-box;
    margin-bottom: 90px;
    display: flex;
    &-left {
      display: flex;
      width: 30%;
      height: 100%;

      flex-direction: column;
      justify-content: space-around;
      text-align: right;
      div {
        color: #ffffff;
        font-size: 18px;
        span {
          color: #0fe5f0;
          font-size: 24px;
        }
      }
    }
    &-center {
      flex: 1;
      width: 100%;
      height: 100%;
      .landingale {
        margin-top: 20px;
        width: 500px;
        height: 100%;
      }
    }

    &-right {
      width: 30%;
      height: 100%;

      ul {
        width: 100%;
        height: 100%;
        list-style-type: disc;
        padding-left: 20px;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        li {
          color: #feffff;
          font-size: 18px;
          span {
            color: #20eaec;
            font-size: 24px;
          }
        }
      }
    }
  }
}
</style>