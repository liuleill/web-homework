<template>
  <div id="center">
    <div class="up">
      <div class="bg-color-black item" v-for="item in titleItem" :key="item.title">
        <p class="ml-3 colorBlue fw-b">{{item.title}}</p>
        <div>
          <dv-digital-flop :config="item.number" style="width:1.25rem;height:.625rem;" />
        </div>
      </div>
    </div>
    <div class="down">
      <!-- 异常监控 -->
      <div class="ranking bg-color-black">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2 mb-1">异常监测</span>
        <!-- <dv-scroll-ranking-board :config="ranking" style="height:2.75rem" /> -->

        <dv-scroll-board :config="config" style="height:2.75rem" />

      </div>

      
      <div class="percent">
        <div class="item bg-color-black">
          <span>空气湿度</span>
          <CenterChart :id="rate[0].id" :tips="rate[0].tips" :colorObj="rate[0].colorData" />
        </div>
        <div class="item bg-color-black">
          <span>土壤湿度</span>
          <CenterChart :id="rate[1].id" :tips="rate[1].tips" :colorObj="rate[1].colorData" />
        </div>
        <div class="water">
          <dv-water-level-pond :config="water" style="height: 1.5rem" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CenterChart from "@/components/echart/center/centerChartRate";

export default {
  data () {
    return {
      titleItem: [
        {
          title: "空气温度(摄氏度)",
          number: {
            number: [26],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "土壤温度(摄氏度)",
          number: {
            number: [18],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "光照强度(Lx)",
          number: {
            number: [99],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "CO2浓度(ppm)",
          number: {
            number: [744],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "土壤EC(us/cm)",
          number: {
            number: [38],
            toFixed: 1,
            content: "{nt}"
          }
        },
        {
          title: "风力级别",
          number: {
            number: [3],
            toFixed: 1,
            content: "{nt}"
          }
        }
      ],

      config: {
        header: ["","","",""],
        data: [
          ["土壤EC", "200","300-365","13:20"],
          ["土壤湿度", "200","0%-100%","13:34"],
          ["土壤EC", "200","300-365","13:56"],
          ["土壤湿度", "200","100","14:10"],
          ["C02浓度", "200","810ppm-1000ppm","14:35"],
          ["PH值", "200","0-14","14:55"],
          ["光照强度", "79","80Lx-90Lx","15:08"],
          ["土壤EC", "200","300-365","15:35"],
          ["土壤湿度", "200","0%-100%","16:07"],
          ["土壤EC", "200","300-365","16:56"],
          ["C02浓度", "200","810ppm-1000ppm","17:13"],
          ["土壤EC", "200","300-365","17:44"],
        ],
        rowNum: 6, //表格行数
        headerHeight: 10,
        headerBGC: "#0f1325", //表头
        oddRowBGC: "#0f1325", //奇数行
        evenRowBGC: "#171c33", //偶数行
        index: false,
        columnWidth: [79],
        align: ["center"]
      },

      ranking: {
        data: [
          {
            name: "土壤EC",
            value: 200
          },
          {
            name: "南阳",
            value: 120
          },
          {
            name: "西峡",
            value: 78
          },
          {
            name: "驻马店",
            value: 66
          },
          {
            name: "新乡",
            value: 80
          },
          {
            name: "新乡2",
            value: 80
          },
          {
            name: "新乡3",
            value: 80
          },
          {
            name: "新乡4",
            value: 80
          },
          {
            name: "新乡5",
            value: 80
          },
          {
            name: "新乡6",
            value: 80
          },
        ],
        carousel: "single",
        unit: ""
      },
      water: {
        data: [24, 40],
        shape: "roundRect",
        formatter: "{value}%",
        waveNum: 3
      },
      // 通过率和达标率的组件复用数据
      rate: [
        {
          id: "centerRate1",
          tips: 60,
          colorData: {
            textStyle: "#3fc0fb",
            series: {
              color: ["#00bcd44a", "transparent"],
              dataColor: {
                normal: "#03a9f4",
                shadowColor: "#97e2f5"
              }
            }
          }
        },
        {
          id: "centerRate2",
          tips: 40,
          colorData: {
            textStyle: "#67e0e3",
            series: {
              color: ["#faf3a378", "transparent"],
              dataColor: {
                normal: "#ff9800",
                shadowColor: "#fcebad"
              }
            }
          }
        }
      ]
    };
  },
  components: {
    CenterChart
    // centerChart1,
    // centerChart2
  }
};
</script>

<style lang="scss" scoped>
#center {
  display: flex;
  flex-direction: column;
  .up {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 0.0625rem;
      padding-top: 0.2rem;
      margin-top: 0.1rem;
      width: 32%;
      height: 0.875rem;
    }
  }
  .down {
    padding: 0.07rem 0.05rem;
    padding-bottom: 0;
    width: 100%;
    display: flex;
    height: 3.1875rem;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 0.0625rem;
    }
    .ranking {
      padding: 0.125rem;
      width: 59%;
    }
    .percent {
      width: 40%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 50%;
        height: 1.5rem;
        span {
          margin-top: 0.0875rem;
          display: flex;
          justify-content: center;
        }
      }
      .water {
        width: 100%;
      }
    }
  }
}
</style>