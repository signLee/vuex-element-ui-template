<template>
    <div class="">
      <p>homePage</p>
      <el-time-picker
        v-model="value2"
        :picker-options="{
          selectableRange: '18:30:00 - 20:30:00'
        }"
        placeholder="任意时间点">
      </el-time-picker>
      <input type="button" value="增加5" @click="add(5)">
      <input type="button" value="减少2" @click="reduce(2)">
      <span>VUEX测试：现在的数字为{{count}}</span>
      <div class="fl">共用样式重置测试</div>
      <router-link to="test">去测试页</router-link>
    </div>
</template>

<script type="text/ecmascript-6">
  import { TimePicker } from 'element-ui';
  import { format } from 'assets/js/utils';
  import {mapGetters, mapActions,mapMutations} from 'vuex'
  export default {
    data: function () {
      return {
         value2: new Date(2016, 9, 10, 18, 40)
      }
    },
    computed: mapGetters([
      'count'
    ]),//从getter.js获取数据属性
    methods: {
      ...mapMutations({
        'increment':'INCREMENT',
        'decrement':'DECREMENT',
      }),//提交function到action.js
      add(val){
        this.increment(val);//这里可以直接调用从mapMutations里引入的方法
      },
      reduce(val){
        this.decrement(val)
      }
    },
    components: {TimePicker},
    mounted(){
      console.log(format(new Date()))
    }
  }
</script>

<style >
</style>
