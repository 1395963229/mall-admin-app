<template>
  <div class="home-container">
    <div class="menu">
      <a-menu
        :default-selected-keys="['1']"
        :default-open-keys="['sub1']"
        mode="inline"
        theme="dark"
        :inline-collapsed="collapsed"
      >
        <a-menu-item key="1">
          <a-icon type="pie-chart" />
          <span>Option 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="desktop" />
          <span>Option 2</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon type="inbox" />
          <span>Option 3</span>
        </a-menu-item>
        <a-sub-menu key="sub1">
          <span slot="title"><a-icon type="mail" /><span>Navigation One</span></span>
          <a-menu-item key="5"> Option 5 </a-menu-item>
          <a-menu-item key="6"> Option 6 </a-menu-item>
          <a-menu-item key="7"> Option 7 </a-menu-item>
          <a-menu-item key="8"> Option 8 </a-menu-item>
        </a-sub-menu>
        <a-sub-menu key="sub2">
          <span slot="title"><a-icon type="appstore" /><span>Navigation Two</span></span>
          <a-menu-item key="9"> Option 9 </a-menu-item>
          <a-menu-item key="10"> Option 10 </a-menu-item>
          <a-sub-menu key="sub3" title="Submenu">
            <a-menu-item key="11"> Option 11 </a-menu-item>
            <a-menu-item key="12"> Option 12 </a-menu-item>
          </a-sub-menu>
        </a-sub-menu>
      </a-menu>
    </div>
    <div :class="{ main: true, 'menu-unfold': collapsed }">
      <div class="main-header">
        <a-button type="primary" style="margin-bottom: 16px" @click="toggleCollapsed">
          <a-icon :type="collapsed ? 'menu-unfold' : 'menu-fold'" />
        </a-button>
        <div class="nav">
          <a-breadcrumb-item>主页</a-breadcrumb-item>
          <a-breadcrumb-item><a href="">xxx</a></a-breadcrumb-item>
        </div>
        <ul class="user-info">
          <li>
            欢迎：xxxxx
            <a-icon type="down" />
          </li>
          <li>退出</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false,
    };
  },
  methods: {
    toggleCollapsed() {
      this.collapsed = !this.collapsed;
    },
  },
};
</script>

<style lang="less" scoped>
.menu {
  width: 180px;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  .ant-menu {
    height: 100%;
  }
}
.main {
  margin-left: 180px;
  transition: all 0.3s;
  &.menu-unfold {
    margin-left: 80px;
  }
  .main-header {
    position: relative;
    height: 50px;
    padding: 10px;
    border-bottom: 1px solid #eee;
    .nav,
    .user-info {
      display: inline-block;
      margin-left: 10px;
    }
    .user-info {
      line-height: 50px;
      position: absolute;
      right: 20px;
      top: 0;
      text-align: center;
      cursor: pointer;
      li {
        padding: 0 20px;
      }
      li:not(:first-child) {
        display: none;
      }
      &:hover {
        li {
          display: block;
        }
        li:not(:first-child):hover {
          background-color: #eee;
          font-weight: 700;
        }
      }
    }
  }
}
</style>
