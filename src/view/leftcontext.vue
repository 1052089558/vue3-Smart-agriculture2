<template>
  <div class="left">
    <div class="left-top">
      <p class="font">{{lefttitle}}</p>
      <div class="datebottom"><span class="selecthalf"
              :class="{'dateclass':isActive==true}"
              @click="Datechangehalf">近半年</span>
        <span @click="Datechangeyear"
              class="selectyear"
              :class="{'dateclass':isActive==false}">近一年</span>
      </div>
      <div class="lineecheat"
           ref="lineecheat"></div>
    </div>
    <div class="left-bottom">
      <p class="font2">{{bottomtitle}}</p>
      <div class="left-bottom-top">
        <div class="left-bottom-top-left">
          <p class="left-bottom-top-left-font">培育一期</p>
          <div class="left-bottom-top-left-proper">
            <div>
              <div :style="{color:'#43638d','font-size':'14px'}">营养液使用量 </div>
              <span :style="{color:'#FFFFFF','font-size':'20px'}">95KG</span>
            </div>
            <div class="lengthdate">
              <div :style="{color:'#43638d','font-size':'14px'}">培育时长</div>
              <span :style="{color:'#FFFFFF','font-size':'20px'}">25天</span>
            </div>

          </div>
          <div class="radarecheat" :style="{'margin-top':'32px'}"></div>
        </div>
        <div class="left-bottom-top-right">
          <p class="left-bottom-top-right-font">培育二期</p>
          <div class="left-bottom-top-right-proper">
            <div>
              <div :style="{color:'#43638d','font-size':'14px'}">营养液使用量 </div>
              <span :style="{color:'#FFFFFF','font-size':'20px'}">95KG</span>
            </div>
            <div class="lengthdate">
              <div :style="{color:'#43638d','font-size':'14px'}">培育时长 </div>
              <span :style="{color:'#FFFFFF','font-size':'20px'}">25天</span>
            </div>

          </div>
          <div class="radarecheat2" :style="{'margin-top':'32px'}"></div>
        </div>
      </div>
      <div class="left-bottom-bottom">
        <div class="radarecheat3"></div>
        <div class="left-bottom-bottom-right">
          <div :style="{color:'#FFFFFF','font-size':'18px'}">培育三期</div>
          <div :style="{color:'#43638d','font-size':'14px','margin-top':'10px'}">培养液使用量</div>
          <div :style="{color:'#FFFFFF','font-size':'20px'}">95KG</div>
          <div :style="{color:'#43638d','font-size':'14px','margin-top':'10px'}">培育时长</div>
          <div :style="{color:'#FFFFFF','font-size':'20px'}">25天</div>
        </div>
      </div>
    </div>
  </div>

</template>

<script >
import { onMounted, reactive, ref, toRefs } from "vue";
import * as echarts from 'echarts';
export default {
  setup (props, context) {
    let state = reactive({
      lefttitle: "菜品产量",
      bottomtitle: "菜品营养成分",
      date: [
        "1月",
        "2月",
        "3月",
        "4月",
        "5月",
        "6月",
        
      ],
      nutritionfacts: [
      ],

      isActive: true,
    });
    onMounted(() => {
      setTimeout(() => { initEcharts(); }, 500)
    })
    const initEcharts = () => {

      const myechart = echarts.init(document.querySelector('.lineecheat'));
      const myechart2 = echarts.init(document.querySelector('.radarecheat'));
      const myechart3 = echarts.init(document.querySelector('.radarecheat2'));
      const myechart4 = echarts.init(document.querySelector('.radarecheat3'));
      myechart.setOption({
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['一期', '二期', '三期']
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        // toolbox: {
        //   feature: {
        //     saveAsImage: {}
        //   }
        // },
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data: state.date
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            name: '一期',
            type: 'line',
            stack: 'Total',
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: '二期',
            type: 'line',
            stack: 'Total',
            data: [220, 182, 191, 234, 290, 330, 310]
          },
          {
            name: '三期',
            type: 'line',
            stack: 'Total',
            data: [150, 232, 201, 154, 190, 330, 410]
          },

        ]

      });
      myechart2.setOption({

        // legend: {
        //   data: ['Allocated Budget', 'Actual Spending']
        // },
        radar: {
          // shape: 'circle',
          indicator: [
          { name: `钙\n32%`, max: 6500, },
            { name: '钾\n11%', max: 16000 },
            { name: '铁\n12%', max: 30000 },
            { name: '其他\n9%', max: 38000 },
            { name: '镁\n5%', max: 52000 },
            { name: '磷\n3%', max: 25000 }
          ],
          name: {
            textStyle: {
              padding: [-20, -10]   // 控制文字padding
            }
          }
        },
        textStyle: {
          color: "#d8dadd"
        },
        series: [
          {
            name: 'Budget vs spending',
            type: 'radar',
            data: [
            
              {
                value: [5000, 14000, 28000, 26000, 42000, 21000],
                name: 'Actual Spending'
              }
            ]
          }
        ]
      })
      //右边
      myechart3.setOption({
        radar: {
          indicator: [
            { name: `钙\n32%`, max: 6500, },
            { name: '钾\n11%', max: 16000 },
            { name: '铁\n12%', max: 30000 },
            { name: '其他\n9%', max: 38000 },
            { name: '镁\n5%', max: 52000 },
            { name: '磷\n3%', max: 25000 }
          ],
          name: {
            textStyle: {
              padding: [-20, -10]   // 控制文字padding
            }
          }
        },
        textStyle: {
          color: "#d8dadd"
        },
        series: [
          {
            name: 'Budget vs spending',
            type: 'radar',
            data: [
              {
                value: [4200, 3000, 20000, 35000, 50000, 18000],
                name: 'Allocated Budget'
              },
            
            ]
          }
        ]
      })
      myechart4.setOption({

        radar: {
          indicator: [
          { name: `钙\n32%`, max: 6500, },
            { name: '钾\n11%', max: 16000 },
            { name: '铁\n12%', max: 30000 },
            { name: '其他\n9%', max: 38000 },
            { name: '镁\n5%', max: 52000 },
            { name: '磷\n3%', max: 25000 }
          ],
          name: {
            textStyle: {
              padding: [-20, -10]  // 控制文字padding
            }
          }

        },
        textStyle: {
          color: "#d8dadd"
        },
        series: [
          {
            name: 'Budget vs spending',
            type: 'radar',
            data: [
              {
                value: [4200, 3000, 20000, 35000, 50000, 18000],
                name: 'Allocated Budget'
              },
           
            ]
          }
        ]
      });

    }
    const Datechangehalf = () => {
      state.isActive = true;
      state.date = [
        "1月",
        "2月",
        "3月",
        "4月",
        "5月",
        "6月",
      ];
      initEcharts();
    }
    const Datechangeyear = () => {
      state.isActive = false;
      state.date = [
        "1月",
        "2月",
        "3月",
        "4月",
        "5月",
        "6月",
        "7月",
        "8月",
        "9月",
        "10月",
        "11月",
        "12月",
      ]
      state.date = state.date.slice();
      initEcharts();
    }
    return {
      ...toRefs(state),
      initEcharts,
      Datechangeyear,
      Datechangehalf,
    }
  }

}
</script>

<style lang="less" scoped>
.left {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  
  &-top {
    height: 315px;
    margin-top: 20px;

    box-sizing: border-box;
    margin-left: 20px;
    margin-right: 20px;
    background-image: url("../assets/lefttopbottom.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .font {
      font-size: 24px;
      color: #0fe5f0;
      margin-left: 20px;
      margin-top: 10px;
    }
    .lineecheat {
      height: 260px;
      width: 450px;
  
    }
    .selecthalf{
      cursor: pointer;
      width: 50%;

   
    }
    .selectyear{
      
      cursor: pointer;
      width: 50%;

    }
    .datebottom {
     display: inline-block;
    width: 96px;
    color: #fffefe;
    margin-left: 75%;
    background-color: #106875;
      .dateclass {
        background-color: #0fe5f0;
        width: 100%;
        height: 100%;
      }
    }
  }
  &-bottom {
    flex: 1;
    margin-top: 20px;
    margin-bottom: 90px;
    // border: 2px solid #106875;
    box-sizing: border-box;
    margin-left: 20px;
    margin-right: 20px;
    background-image: url("../assets/lefttopbottom.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .font2 {
      font-size: 24px;
      color: #0fe5f0;
      margin-left: 20px;
      margin-top: 12px;
    }
    &-top {
      display: flex;

      width: 100%;
      height: 56%;
      overflow: hidden;
      &-left {
        width: 45%;
        height: 100%;
        margin-left: 45px;
        margin-top: 5px;
        overflow: hidden;
        &-font {
          margin-bottom: 10px;
          color: #ffffff;
          font-size: 18px;
        }
        &-proper {
          display: flex;
          .lengthdate {
            margin-left: 26px;
          }
        }
        .radarecheat {
          width: 160px;
          height: 160px;
         
        }
      }
      &-right {
        width: 45%;
        height: 100%;
        margin-top: 5px;
        overflow: hidden;
        &-proper {
          display: flex;
          .lengthdate {
            margin-left: 26px;
          }
        }
        &-font {
          margin-bottom: 10px;
          color: #ffffff;
          font-size: 18px;
        }
        .radarecheat2 {
          width: 160px;
          height: 160px;
        
        }
      }
    }
    &-bottom {
      height: 44%;
      width: 100%;
      display: flex;

      .radarecheat3 {
        width: 160px;
        height: 160px;
        margin-left: 90px;
      
      }
      &-right{
        flex-direction: column;
       
        padding-left: 40px;
        margin-top: 14px;
      }
    }
  }
}
</style>