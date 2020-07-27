<template>
  <div class="order-list">
    <div class="list-search">
      <el-row>
        <el-col>
          <div class="search-simple">
            <el-row :gutter="40">
              <el-col :span="6">
                <span>客户名称：</span
                ><el-input
                  placeholder="请输入内容"
                  size="mini"
                  v-model="search.name"
                ></el-input>
              </el-col>
              <el-col :span="6">
                <span>客户名称：</span
                ><el-input placeholder="请输入内容" size="mini"></el-input>
              </el-col>
              <el-col :span="6">
                <span>客户名称：</span
                ><el-input placeholder="请输入内容" size="mini"></el-input>
              </el-col>
              <el-col :span="6">
                <span>客户名称：</span
                ><el-input placeholder="请输入内容" size="mini"></el-input>
              </el-col>
            </el-row>
          </div>
          <el-collapse-transition>
            <div class="search-simple search-full" v-show="show">
              <el-row :gutter="40">
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
                <el-col :span="6">
                  <span>客户：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
              </el-row>
              <el-row :gutter="40">
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
                <el-col :span="6">
                  <span>客户名称：</span
                  ><el-input placeholder="请输入内容" size="mini"></el-input>
                </el-col>
              </el-row>
            </div>
          </el-collapse-transition>
        </el-col>
      </el-row>
      <el-row :gutter="15" class="button-group">
        <el-col :span="12">
          <el-button
            @click="open"
            size="mini"
            type="warning"
            style="float:right"
            >查询</el-button
          ></el-col
        >
        <el-col :span="12">
          <el-button size="mini" type="info">清空</el-button></el-col
        >
      </el-row>
    </div>
    <div class="list-search-button" @click="open">
      <i :class="listSearchButtonIcon"></i>
    </div>
    <div class="list-main">
      <el-row>
        <el-col class="main-button"
          ><el-button type="primary" size="mini">新增</el-button>
          <el-button type="success" size="mini">新增</el-button>
          <el-button type="info" size="mini">新增</el-button></el-col
        >
        <el-col class="main-table">
          <el-table :data="tableData" stripe size="mini" style="width: 100%">
            <el-table-column type="selection" width="55"> </el-table-column>
            <el-table-column prop="date" label="日期"> </el-table-column>
            <el-table-column prop="name" label="姓名"> </el-table-column>
            <el-table-column prop="name" label="地址"> </el-table-column>
            <el-table-column prop="name" label="地址"> </el-table-column>
            <el-table-column prop="name" label="地址"> </el-table-column>
            <el-table-column prop="address" label="地址"> </el-table-column>
          </el-table>
        </el-col>
        <el-col class="page">
          <span>每页显示条数：</span>
          <el-select v-model="pageNum" placeholder="请选择" size="mini">
            <el-option
              v-for="item in pageNums"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            >
            </el-option>
          </el-select>
          <el-pagination background layout="prev, pager, next" :total="1000">
          </el-pagination>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      listSearchButtonIcon: "el-icon-arrow-down",
      search: {
        name: ""
      },
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ],
      pageNum: 10,
      pageNums: [
        {
          value: 10,
          label: "10"
        },
        {
          value: 20,
          label: "20"
        },
        {
          value: 30,
          label: "30"
        }
      ]
    };
  },
  methods: {
    open() {
      this.show = !this.show;
      if (this.listSearchButtonIcon == "el-icon-arrow-down") {
        this.listSearchButtonIcon = "el-icon-arrow-up";
      } else {
        this.listSearchButtonIcon = "el-icon-arrow-down";
      }
    }
  }
};
</script>
<style scoped lang="scss">
.order-list {
  .list-search {
    background-color: #fff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12), 0 0 16px rgba(0, 0, 0, 0.06);
    padding-top: 2vmin;
    .search-simple {
      padding: 0 5vmin 0 2.5vmin;
      .el-row {
        padding: 0.8vmin 0;
        .el-col {
          span {
            width: 30%;
            float: left;
            text-align: right;
            line-height: 27px;
          }
          .el-input {
            width: 70%;
            display: block;
            float: left;
          }
        }
      }
    }
    .button-group {
      padding: 1vmin 0 1.8vmin 0;
    }
  }
  .list-search-button {
    width: 92px;
    height: 18px;
    margin: auto;
    background-image: url("../assets/images/main/list-search-button.png");
    text-align: center;
  }
  .list-main {
    background-color: #fff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12), 0 0 16px rgba(0, 0, 0, 0.06);
    min-height: 60vmin;
    margin-top: 2vmin;
    margin-bottom: 1vmin;
    .main-button {
      .el-button {
        margin: 2vmin 1vmin;
      }
      .el-button:nth-child(1) {
        margin-left: 4vmin;
      }
    }
    .main-table {
      padding: 1vmin 4vmin;
    }
    .page {
      span {
        float: left;
        padding: 2vmin 0 2vmin 4vmin;
        font-size: 1.4vmin;
      }
      .el-select {
        float: left;
        width: 70px;
        padding: 1.3vmin 0 2vmin 0vmin;
      }
      .el-pagination {
        float: right;
        padding: 1.5vmin 4vmin 3vmin 0;
      }
    }
  }
}
</style>
