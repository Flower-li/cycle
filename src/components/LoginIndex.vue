<template>
  <div class="login-index">
    <div class="header">
      <el-row :gutter="40">
        <el-col :span="6"
          ><div class="header-list">
            <el-button
              type="warning"
              icon="el-icon-document-copy"
              circle
            ></el-button
            ><br />
            <el-link type="warning" :underline="false">34234</el-link>
            <h5>数据统计</h5>
          </div></el-col
        >
        <el-col :span="6"
          ><div class="header-list">
            <el-button type="danger" icon="el-icon-pie-chart" circle></el-button
            ><br />
            <el-link type="danger" :underline="false">12331</el-link>
            <h5>数据统计</h5>
          </div></el-col
        >
        <el-col :span="6"
          ><div class="header-list">
            <el-button
              type="success"
              icon="el-icon-data-analysis"
              circle
            ></el-button
            ><br />
            <el-link type="success" :underline="false">123</el-link>
            <h5>数据统计</h5>
          </div></el-col
        >
        <el-col :span="6"
          ><div class="header-list">
            <el-button type="primary" icon="el-icon-files" circle></el-button
            ><br />
            <el-link type="primary" :underline="false">12414</el-link>
            <h5>数据统计</h5>
          </div></el-col
        >
      </el-row>
    </div>
    <div class="main">
      <el-row :gutter="15">
        <el-col :span="11">
          <div class="main-left">
            <h1>功能菜单</h1>
            <el-table :data="tableData" stripe size="mini" style="width: 100%">
              <el-table-column prop="date" label="日期"> </el-table-column>
              <el-table-column prop="name" label="姓名"> </el-table-column>
              <el-table-column prop="address" label="地址"> </el-table-column>
              <el-table-column label="预警等级" width="200" align="center"
                ><el-tag type="danger" size="small" effect="dark">标签</el-tag>
              </el-table-column>
            </el-table>
          </div>
        </el-col>
        <el-col :span="13">
          <div class="main-right">
            <div class="right-top">
              <h1>系统公告</h1>
              <ul>
                <li>
                  <a href="">因为什么可是对方那块绿色的蒋副快乐</a
                  ><span>2020-12-12</span>
                </li>
                <li>
                  <a href="">因为什么可是对方那块绿色的蒋副快乐</a
                  ><span>2020-12-12</span>
                </li>
                <li>
                  <a href="">因为什么可是对方那块绿色的蒋副快乐</a
                  ><span>2020-12-12</span>
                </li>
              </ul>
            </div>
            <div class="right-bottom">
              <div id="main"></div>
            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginIndex",
  data() {
    return {
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市 1516 弄"
        }
      ]
    };
  },
  mounted() {
    this.myEcharts();
  },
  methods: {
    myEcharts() {
      // 基于准备好的dom，初始化echarts实例
      var myChart = this.$echarts.init(document.getElementById("main"));

      // 指定图表的配置项和数据
      var option = {
        title: {
          text: "每日销量",
          textStyle: {
            fontSize: 17,
            color: "#000000"
          }
        },
        grid: {
          left: "2%",
          right: "3%",
          bottom: "8%",
          top: "20%",
          containLabel: true
        },
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "cross",
            label: {
              backgroundColor: "#f56c6c"
            }
          }
        },
        xAxis: {
          type: "category",
          boundaryGap: false,
          data: ["06-12", "06-13", "06-14", "06-15", "06-16", "06-17", "06-18"]
        },
        yAxis: {
          type: "value"
        },
        series: [
          {
            data: [820, 932, 901, 934, 1290, 1330, 1320],
            type: "line",
            areaStyle: {
              color: new this.$echarts.graphic.LinearGradient(
                0,
                1,
                0,
                0,
                [
                  {
                    offset: 0,
                    color: "rgba(255, 255, 255, 0)"
                  },
                  {
                    offset: 1,
                    color: "#f56c6c"
                  }
                ],
                false
              )
            },
            itemStyle: {
              normal: {
                color: "#f56c6c", //改变折线点的颜色
                lineStyle: {
                  color: "#f56c6c" //改变折线颜色
                }
              }
            }
          }
        ]
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    }
  }
};
</script>

<style lang="scss" scoped>
.login-index {
  .header {
    .el-row {
      .el-col {
        .header-list {
          background-color: #fff;
          height: 30vmin;
          box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12),
            0 0 16px rgba(0, 0, 0, 0.06);
          text-align: center;
          .el-button {
            font-size: 4.5vmin;
            padding: 2.5vmin;
            margin-top: 5vmin;
          }
          .el-link {
            font-size: 3.5vmin;
            margin-top: 2vmin;
            margin-bottom: 0.3vmin;
          }
          h5 {
            color: #b4b4b4;
            font-weight: normal;
          }
        }
      }
    }
  }
  .main {
    margin-top: 3vmin;
    .main-left {
      background-color: #fff;
      height: 46.5vmin;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12), 0 0 16px rgba(0, 0, 0, 0.06);
      h1 {
        font-size: 1.7vmin;
        padding: 2vmin 3.5vmin;
      }
      .el-table {
        padding: 0 3vmin;
        max-height: 37vmin;
        overflow: auto;
      }
      .el-table::-webkit-scrollbar {
        display: none;
      }
      .el-table::before {
        height: 0px;
      }
    }
    .main-right {
      height: 47.5vmin;
      .right-top {
        height: 20vmin;
        background-color: #fff;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12), 0 0 16px rgba(0, 0, 0, 0.06);
        h1 {
          font-size: 1.7vmin;
          padding: 2vmin 2.5vmin 1vmin 2.5vmin;
          color: #777c82;
        }
        ul {
          padding: 0 2.5vmin;
          li {
            padding: 1vmin 0;
            border-bottom: 1px dotted #777c82;
            a {
              color: #777c82;
            }
            span {
              color: #777c82;
              float: right;
            }
          }
        }
      }
      .right-bottom {
        height: 23.5vmin;
        margin-top: 3vmin;
        background-color: #fff;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12), 0 0 16px rgba(0, 0, 0, 0.06);
        #main {
          width: 95%;
          height: 93%;
          padding: 2vmin 0 0 2.5vmin;
        }
      }
    }
  }
}
</style>
