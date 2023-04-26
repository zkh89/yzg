<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <div class="home">
      <div style="width: 100%">
        <el-row
          :gutter="20"
          style="margin-bottom: 20px; justify-content: space-around"
        >
          <el-col :span="6" v-for="item in box" :key="item.title">
            <!-- 卡片组件 -->
            <Card :cardData="item"></Card>
          </el-col>
        </el-row>
        <LineCharts :options="echartsObj"></LineCharts>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import LineCharts from '@/components/LineCharts.vue'
import { Options, Vue } from "vue-class-component";

@Options({
  components: {},
})
export default class HomeView extends Vue {

}
</script>
