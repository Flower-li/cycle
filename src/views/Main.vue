<template>
  <div class="Main">
    <el-container>
      <el-aside width="200px">
        <div class="logo-img"><span>logo</span></div>
        <el-menu
          default-active="1-1"
          class="el-menu-vertical-demo"
          :collapse="isCollapse"
          background-color="#2b333e"
          text-color="#fff"
          active-text-color="#E6A23C"
        >
          <el-submenu
            v-for="(item, index) in navList"
            :key="index"
            :index="item.index"
          >
            <template slot="title">
              <i :class="item.icon"></i>
              <span slot="title">{{ item.title }}</span>
            </template>
            <el-menu-item
              v-for="(itemChild, indexChild) in item.children"
              :key="indexChild"
              :index="itemChild.index"
              @click="navClick(itemChild)"
              >{{ itemChild.title }}</el-menu-item
            >
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-container>
        <el-header>
          <el-button @click="ChangeNav" class="change-nav"
            ><i class="el-icon-s-operation"></i
          ></el-button>
          <el-breadcrumb separator-class="el-icon-arrow-right">
            <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
            <el-breadcrumb-item>活动管理</el-breadcrumb-item>
            <el-breadcrumb-item>活动列表</el-breadcrumb-item>
            <el-breadcrumb-item>活动详情</el-breadcrumb-item>
          </el-breadcrumb>
          <el-dropdown>
            <span class="el-dropdown-link">
              系统管理员<i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>修改密码</el-dropdown-item>
              <el-dropdown-item>退出登陆</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <el-input
            placeholder="请输入内容"
            v-model="input3"
            class="input-with-select"
          >
            <el-select v-model="select" slot="prepend" placeholder="请选择">
              <el-option label="姓名" value="1"></el-option>
              <el-option label="手机号" value="2"></el-option>
              <el-option label="地址" value="3"></el-option>
            </el-select>
            <el-button slot="append" icon="el-icon-search"></el-button>
          </el-input>
        </el-header>
        <el-main>
          <el-tabs v-model="editableTabsValue" closable @tab-remove="removeTab">
            <el-tab-pane
              v-for="(item, index) in editableTabs"
              :key="index"
              :label="item.title"
              :name="item.name"
            >
              <AsyncComponent :componentPath="item.component"></AsyncComponent>
            </el-tab-pane>
          </el-tabs>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import AsyncComponent from "@/components/AsyncComponent.vue";
export default {
  name: "Main",
  components: {
    AsyncComponent
  },
  data() {
    return {
      isCollapse: false,
      input3: "",
      select: "姓名",
      editableTabsValue: "1",
      editableTabs: [
        {
          title: "首页",
          name: "1",
          component: "components/LoginIndex"
        }
      ],
      tabIndex: 1,
      navList: [
        {
          title: "订单管理",
          index: "1",
          icon: "el-icon-s-order",
          children: [
            {
              title: "订单明细",
              index: "1-1",
              component: "components/OrderList"
            },
            {
              title: "订单明细2",
              index: "1-2",
              component: "components/OrderList"
            }
          ]
        },
        {
          title: "配送单",
          index: "2",
          icon: "el-icon-s-flag",
          children: [
            {
              title: "配送单明细",
              index: "2-1",
              component: "components/DistributionList"
            },
            {
              title: "配送单明细2",
              index: "2-2",
              component: "components/DistributionList"
            }
          ]
        }
      ]
    };
  },
  methods: {
    ChangeNav() {
      this.isCollapse = !this.isCollapse;
    },
    removeTab(targetName) {
      let tabs = this.editableTabs;
      let activeName = this.editableTabsValue;
      if (activeName === targetName) {
        tabs.forEach((tab, index) => {
          if (tab.name === targetName) {
            let nextTab = tabs[index + 1] || tabs[index - 1];
            if (nextTab) {
              activeName = nextTab.name;
            }
          }
        });
      }

      this.editableTabsValue = activeName;
      this.editableTabs = tabs.filter(tab => tab.name !== targetName);
    },
    navClick(onComponent) {
      let existTab = this.editableTabs.find(f => f.name === onComponent.index);
      if (existTab) {
        this.editableTabsValue = onComponent.index;
      } else {
        this.editableTabs.push({
          title: onComponent.title,
          name: onComponent.index,
          component: onComponent.component
        });
        this.editableTabsValue = onComponent.index;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.Main {
  height: 100%;
  .el-container {
    height: 100%;
    .el-aside {
      background-color: #2b333e;
      height: 100%;
      width: auto !important;
      .logo-img {
        width: 100%;
        height: 60px;
        text-align: center;
        font-weight: bold;
        span {
          font-size: 4vmin;
          line-height: 60px;
          color: #fff;
        }
      }
      .el-menu {
        border-right: 0px solid #fff;
      }
      .el-menu-vertical-demo:not(.el-menu--collapse) {
        width: 199px;
        min-height: 400px;
        overflow: hidden;
      }
      .el-menu--collapse {
        width: unset;
      }
      .el-menu-item {
        background-color: rgb(34, 41, 50) !important;
      }
    }
    .el-header {
      border-bottom: 0px solid #2b333e;
      .change-nav {
        margin-top: 13px;
        padding: 5px 8px;
        float: left;
        i {
          font-size: 20px;
        }
      }
      .el-breadcrumb {
        float: left;
        margin: 22px 0 0 20px;
      }
      .el-input {
        width: 550px;
        margin-top: 9px;
        float: right;
        .el-select {
          width: 130px;
        }
      }
      .el-dropdown {
        float: right;
        margin: 19px 0 0 20px;
      }
    }
    .el-main {
      background-color: #f8f8f8;
      padding: 0 20px 20px 20px;
    }
  }
}
</style>
<style lang="scss">
.Main {
  height: 100%;
  .el-container {
    .el-tabs__item.is-active {
      color: #e6a23c;
    }
    .el-tabs__active-bar {
      background-color: #e6a23c;
    }
  }
}
</style>
