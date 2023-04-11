<template>
  <div class="home">
    <div class="titleName">{{ title }}</div>
    <div class="box">
      <div class="box-left">
        <leftcontext></leftcontext>
      </div>
      <div class="box-center">
        <centercontext></centercontext>
      </div>
      <div class="box-right">
       <rightcontext></rightcontext>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
import leftcontext from './leftcontext.vue';
import centercontext from './centercontext.vue'
import rightcontext from './rightcontext.vue'
export default {
  components: { leftcontext,centercontext,rightcontext },
  setup (props, context) {
    let state = reactive({
      title: "智慧农业数据展示平台",
   
    });
    return {
      ...toRefs(state),
    };
  },
};
</script>

<style lang="less" >
html,
body,
#app {
  width: 100%;
  height: 100%;
  overflow: hidden;
  background-color: #010C1E;
}

.home {
  width: 100%;
  height: 100%;
  .titleName {
    text-align: center;
    line-height: 73px;
    font-size: 30px;
    height: 73px;
    background-image: url('../assets/title.png.png');
    letter-spacing: 10px;
    color: #ffffff;
    font-weight:900;
  }
  .box {
    height: 100%;
    width: auto;
    display: flex;
    background-repeat: no-repeat;
    overflow: hidden;
    &-left {
      width: 500px;
    }
    &-center {
      flex: 1;
    }
    &-right {
      width: 500px;
    }
  }
}
</style>