<template>
  <div class="right">
    <div class="right-top">
      <p class="font">{{toptitle}}</p>
      <div class="right-top-context">
        <div class="right-top-context-left">

          <div>
            <img :src="temperature"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">空气温度:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">30℃</span>
          </div>
          <div>
            <img :src="humidity"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">空气湿度:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">70℃</span>
          </div>
          <div>
            <img :src="windspeed"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px',display:'inline-block','margin-left':'46px'}">风速:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">7</span>
          </div>
          <div>
            <img :src="winddirection"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px',display:'inline-block','margin-left':'46px'}">风向:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">5</span>
          </div>

        </div>
        <div class="right-top-context-right">

          <div>
            <img :src="pressure"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">大气压力:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">3</span>
          </div>
          <div>
            <img :src="strength"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">光照强度:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">6</span>
          </div>
          <div>
            <img :src="radiation"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px',display:'inline-block','margin-left':'26px'}">光辐射:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">10</span>
          </div>
          <div>
            <img :src="rainfall"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px',display:'inline-block','margin-left':'26px'}">降雨量:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">4</span>
          </div>

        </div>
      </div>

    </div>
    <div class="right-center">
      <p class="font2">{{centertitle}}</p>
      <div class="right-top-context">
        <div class="right-top-context-left">

          <div>
            <img :src="nutrientsolution"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px',display:'inline-block','margin-left':'28px'}">营养液:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">10</span>
          </div>
          <div>
            <img :src="temperature"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">室内温度:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">25℃</span>
          </div>
          <div>
            <img :src="humidity"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">空气湿度:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">62%</span>
          </div>

        </div>
        <div class="right-top-context-right">

          <div>
            <img :src="lightintensity"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">灯光强度:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">8</span>
          </div>
          <div>
            <img :src="radiation"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px',display:'inline-block','margin-left':'28px'}">光辐射:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">10</span>
          </div>
          <div>
            <img :src="pressure"
                 width="30"
                 height="30">
            <span :style="{color:'#FFFFFF','fontSize':'18px'}">室内气压:</span>
            <span :style="{color:'#0FE5F0','fontSize':'24px'}">3</span>
          </div>

        </div>
      </div>
    </div>
    <div class="right-bottom">
      <p class="font3">{{bottomtitle}}</p>
      <div class="right-bottom-context">
        <ul class="right-bottom-context-proto">
          <li>
            砷
          </li>
          <li>
            镉
          </li>
          <li>
            汞
          </li>
          <li>
            铅
          </li>
          <li>
            铬
          </li>
          <li>
          </li>

        </ul>
        <div class="lineclass"></div>
        <div v-for="(item, index) in protodata"
             :key="index"
             class="prototable">
          <div class="prototableitem">
            <span> {{item [0]}}</span>
            <span>{{item [1]}}</span>
            <span>{{item [2]}}</span>
            <span>{{item [3]}}</span>
            <span>{{item [4]}}</span>
            <span class="unit"> {{item [5]}}</span>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import temperature from '../assets/SVG/temperature.svg'
import humidity from '../assets/SVG/humidity.svg'
import windspeed from '../assets/SVG/风速.svg'
import winddirection from '../assets/SVG/风向.svg'
import strength from '../assets/SVG/光照强度.svg'
import { toRefs, reactive } from '@vue/reactivity';
import pressure from '../assets/SVG/大气压力.svg'
import radiation from '../assets/SVG/光辐射.svg'
import rainfall from '../assets/SVG/降雨量.svg'
import nutrientsolution from '../assets/SVG/营养液.svg'
import lightintensity from '../assets/SVG/灯光强度.svg'
export default {
  setup (props, context) {
    let state = reactive({
      toptitle: "园区气候检测",
      centertitle: "大棚环境监测",
      bottomtitle: "监测样品描述",
      protodata: [[
        "ND",
        "ND",
        "ND",
        "ND",
        "ND",
        "(mg/kg)",
      ],
      [
        "0.02",
        "0.02",
        "0.01",
        "0.02",
        "0.01",
        "定量限"
      ]
      ]
    });
    return {
      ...toRefs(state),
      temperature,
      humidity,
      windspeed,
      winddirection,
      pressure,
      strength,
      radiation,
      rainfall,
      nutrientsolution,
      lightintensity
    }
  }
}
</script>

<style lang="less" scoped>
.right {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  &-top {
    flex: 1;
    margin: 20px 20px 20px 20px;
    // border: 2px solid #106875;
    box-sizing: border-box;
    background-image: url("../assets/lefttopbottom.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .font {
      font-size: 24px;
      color: #0fe5f0;
      margin-left: 20px;
      padding-top: 10px;
    }
    &-context {
      display: flex;
      width: 100%;
      height: 86%;
      overflow: hidden;
      &-left {
        padding-left: 30px;
        width: 50%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        span {
          margin-left: 10px;
        }
      }
      &-right {
        width: 50%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        span {
          margin-left: 10px;
        }
      }
    }
  }
  &-center {
    height: 250px;
    margin: 0px 20px 20px 20px;
    // border: 2px solid #106875;
    box-sizing: border-box;
    background-image: url("../assets/lefttopbottom.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .font2 {
      font-size: 24px;
      color: #0fe5f0;
      margin-left: 20px;
      margin-top: 10px;
    }
  }
  &-bottom {
    height: 220px;
    margin: 0px 20px 90px 20px;
    // border: 2px solid #106875;
    box-sizing: border-box;
    background-image: url("../assets/lefttopbottom.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    .font3 {
      font-size: 24px;
      color: #0fe5f0;
      margin-left: 20px;
      margin-top: 10px;
    }
    &-context {
      width: 100%;
      height: 78%;

      &-proto {
        padding-top: 5px;

        display: flex;

        li {
          color: #ffffff;
          padding-left: 48px;
        }
      }
      .lineclass {
        width: 90%;
        height: 1px;
        background: #106875;
        margin-left: 30px;
        margin-top: 5px;
        margin-bottom: 20px;
      }
      .prototable {
        
        width: 100%;
        height: 30px;
    
       .prototableitem{
        span {
          display: inline-block;
          text-align: center;
          color: #0fe5f0;
          margin-left: 40px;
      
        }
       
        .unit {
          color: #ffffff;
        }
       }
      
      
      }
      
    }
  }
}
</style>