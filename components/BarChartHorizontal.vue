<template v-show="$vuetify.breakpoint.lgAndUp">
  <div class="level">
    <div :id="id" style="width: 100%; height: 190px"></div>
  </div>
</template>

<script>
let myChart;
export default {
  data() {
    return {
      option: {
        tooltip: {
          trigger: "axis",
          axisPointer: {
            // Use axis to trigger tooltip
            type: "shadow", // 'shadow' as default; can also be 'line' or 'shadow'
          },
        },
        legend: {
          textStyle: {
            color: "white",
          },
        },
        grid: {
          y: 60,
          y2: 20,
        },
        xAxis: {
          type: "value",
          axisLabel: {
            textStyle: {
              color: "white",
            },
            // interval: 0,
            // rotate: "45",
            clickable: true, //And add click events to the chart to determine where to click based on the return value
            interval: 0,
            formatter: function (params, index) {
              if (index % 2 != 0) {
                return;
                // return "\n\n" + params;
              } else {
                return params;
              }
            },
          },
        },
        yAxis: {
          axisLabel: {
            textStyle: {
              color: "white",
            },
          },
          type: "category",
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        series: [
          {
            name: "Week 1",
            type: "bar",
            stack: "total",
            barGap: "-100%",
            barCategoryGap: "20%",

            label: {
              show: true,
            },
            emphasis: {
              focus: "series",
            },
            data: [197767, 15347, 118843, 77023, 79366, 98499, 90751],
          },
          {
            name: "Week 2",
            type: "bar",
            stack: "total",
            label: {
              show: true,
            },
            emphasis: {
              focus: "series",
            },
            data: [79700, 0, 0, 13632, 0, 0, 46611],
          },
          {
            name: "Week 3",
            type: "bar",
            stack: "total",
            label: {
              show: true,
            },
            emphasis: {
              focus: "series",
            },
            data: [15432, 0, 41836, 0, 0, 0, 46263],
          },
          {
            name: "Week 4",
            type: "bar",
            stack: "total",
            label: {
              show: true,
            },
            emphasis: {
              focus: "series",
            },
            data: [19675, 0, 0, 35002, 43501, 0, 21344],
          },
          {
            name: "Week 5",
            type: "bar",
            stack: "total",
            label: {
              show: true,
            },
            emphasis: {
              focus: "series",
            },
            data: [0, 0, 0, 0, 19342, 32222, 0],
          },
          {
            name: "Week 6",
            type: "bar",
            stack: "total",
            label: {
              show: true,
            },
            emphasis: {
              focus: "series",
            },
            data: [0, 26354, 0, 0, 0, 0, 0],
          },
        ],
      },
    };
  },
  mounted() {
    setTimeout(() => {
      myChart = this.$echarts.init(document.getElementById(this.id));
      myChart.setOption(this.option, true);
      window.addEventListener("resize", function () {
        myChart.resize();
      });
    }, 1);
  },
  // updated() {
  //   const option = {
  //     tooltip: {
  //       trigger: "axis",
  //       axisPointer: {
  //         type: "cross",
  //         crossStyle: {
  //           color: "#999",
  //         },
  //       },
  //     },
  //     // toolbox: {
  //     //   feature: {
  //     //     saveAsImage: { show: true, title: "Save" },
  //     //   },
  //     // },
  //     legend: {
  //       data: ["Min", "Max", "Avg"],
  //       textStyle: {
  //         fontSize: 12,
  //       },
  //     },
  //     xAxis: {
  //       name: this.xAxis,
  //       offset: 20,
  //       nameLocation: "center",
  //       nameTextStyle: {
  //         fontSize: 12,
  //       },
  //       axisLabel: {
  //         fontSize: 12,
  //         verticalAlign: "bottom",
  //       },
  //       type: "category",
  //       data: 10,
  //     },
  //     yAxis: {
  //       nameTextStyle: {
  //         fontSize: 12,
  //       },
  //       name: this.yAxis,
  //       type: "value",
  //       min: 0,
  //       max: this.max,
  //       axisLabel: {
  //         // formatter: "{value} cm",
  //         fontSize: 12,
  //       },
  //     },

  //     series: [
  //       {
  //         //min data set
  //         name: "Min",
  //         data: [10, 20, 30],
  //         type: "line",
  //         fontSize: 30,
  //         color: "#36c25b",
  //         areaStyle: { color: "rgba(135, 211, 124, 1)" },
  //         label: {
  //           color: "black",
  //           fontSize: 15,
  //           formatter: function (d) {
  //             return d.name + d.data;
  //           },
  //         },
  //       },
  //       {
  //         //max data set
  //         name: "Max",
  //         data: [20, 10, 30],
  //         type: "line",
  //         fontSize: 30,
  //         color: "#f52525",
  //         areaStyle: { color: "rgba(246, 36, 89, 0.2)" },
  //         label: {
  //           color: "black",
  //           fontSize: 15,
  //           formatter: function (d) {
  //             return d.name + d.data;
  //           },
  //         },
  //       },
  //       {
  //         //average data set
  //         name: "Avg",
  //         data: [40, 10, 20],
  //         type: "line",
  //         fontSize: 30,
  //         color: "#1930fc",
  //         areaStyle: { color: "rgba(137, 196, 244, 0.5)" },
  //         label: {
  //           color: "black",
  //           fontSize: 15,
  //           formatter: function (d) {
  //             return d.name + d.data;
  //           },
  //         },
  //       },
  //     ],
  //   };
  //   // var myChart = this.$echarts.init(document.getElementById(this.id));
  //   myChart.setOption(option, true);
  //   // console.log(this.data)
  // },
  props: ["id"],
  // props: ["data", "id", "title", "xAxis", "yAxis", "max"],
};
</script>

<style scoped>
.v-card__title {
  font-size: 1rem;
  padding: 8px 10px 8px 20px;
  color: aliceblue;
}

.level {
  /* background-color: white; */
}
</style>
