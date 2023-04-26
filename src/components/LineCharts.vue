<template>
     <div ref="box" style="height: 400px; background-color: #fff; padding: 20px;"></div>
</template>

<script>
    import * as echarts from 'echarts'
export default {
    props:{
        options:{
            type:Object, //数据类型
            default:()=>{},  //设置默认值
            require:true  //是否必传
        }
    },
    mounted(){
        this.drawEcharts(this.options)
    },
    methods:{
        //绘制图表
        drawEcharts(options){
            // 初始化报表
            let echart = echarts.init(this.$refs.box);
            let option = {
                title: {
                text: '堆叠区域图'
            },
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                type: 'cross',
                label: {
                    backgroundColor: '#6a7985'
                }
                }
            },
            legend: {
                data: ['Email', 'Union Ads', 'Video Ads', 'Direct', 'Search Engine']
            },
            toolbox: {
                feature: {
                saveAsImage: {}
                }
            },
            grid: {
                left: '3%',
                right: '4%',
                bottom: '3%',
                containLabel: true
            },
            xAxis: [
                {
                type: 'category',
                boundaryGap: false,
                data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
                }
            ],
            yAxis: [
                {
                type: 'value'
                }
            ],
                // 核心数据
                //  动态传入
                series:options.series
            };
            // 使用配置 生成报表
            echart.setOption(option);
            // resize 自适应
            window.addEventListener('resize', () => {
                echart.resize();
            });
        }
    }
}
</script>

<style>

</style>