<!--
 描述: 产品热词
 作者: Jack Chen
 日期: 2020-05-09
-->

<template>
  <div class="word-container"> 
    <div class="chart" id="chart_right1"></div>
  </div>
</template>

<script>
import '@/assets/js/echarts-wordcloud.min'

export default {
  name: "wordCloud",
  data() {
    return {
      timer: null
    }
  },
  mounted() {
    this.getEchartRight1();
    this.timer = setInterval(() => {
      this.getEchartRight1();
    }, 5000)
  },
  methods: {
    getEchartRight1() {
      let myChart = echarts.init(document.getElementById('chart_right1'));
      let option = {
        // tooltip: {
        //   show: false
        // },
        series: [{
          type: 'wordCloud',
          gridSize: 1,
          sizeRange: [12, 50],
          rotationRange: [-90, 90],
          rotationStep: 45,
          shape: 'diamond',
          width: '90%',
          textPadding: 0,
          autoSize: {
            enable: true,
            minSize: 6
          },
          textStyle: {
            normal: {
              textBorderColor: 'rgba(255,255,255,0.3)',
              textBorderWidth: 1,
              color: () => {
                return 'rgb(' + [
                  Math.round(Math.random() * 160),
                  Math.round(Math.random() * 160),
                  Math.round(Math.random() * 160)
                ].join(',') + ')';
              }
            },
            emphasis: {
              fontSize: 20,
              // shadowBlur: 10,
              // shadowColor: 'rgba(255,255,255, .1)'
            }
          },
          data: [{
            name: '土壤污染',
            value: 810
          }, {
            name: '污染监测',
            value: 520
          },{
            name: "生物特性",
            value: 928
          },{
            name: "土壤功能",
            value: 906
          },{
            name: "公众健康",
            value: 825
          },{
            name: "医疗",
            value: 514
          },{
            name: "质量溯源",
            value: 486
          },{
            name: "实验室分析",
            value: 53
          },{
            name: "采样方法",
            value: 927
          },{
            name: "环境行业",
            value: 1308
          },{
            name: "重金属污染",
            value: 693
          },{
            name: "农药残留",
            value: 611
          },{
            name: "有机污染物",
            value: 512
          },{
            name: "数据共享",
            value: 312
          },{
            name: "敏感目标",
            value: 163
          },{
            name: "土壤修复",
            value: 104
          },{
            name: "在线监测",
            value: 31
          },{
            name: "毒性评价",
            value: 473
          },{
            name: "固化处理",
            value: 207
          },{
            name: "基础层",
            value: 194
          },{
            name: "可视化",
            value: 211
          },{
            name: "化学特性",
            value: 116
          },{
            name: "实验室分析",
            value: 1309
          }]
        }]
      }

      myChart.setOption(option, true);
      window.addEventListener('resize', () => {
        myChart.resize();
      });
    },
  },
  beforeDestroy() {
    clearInterval(this.timer);
  }
};
</script>

<style lang="scss" scoped>
.word-container {
  .chart {
    height: 3rem;
  }
}
</style>
