<template>
  <div style="height:100%">
     <header class="header">
      <div class="logo">
          <span class="big">{{ site.name }}</span>
          <span class="min">{{ site.description }}</span>
        </div>
        <span class="header-btn" @click="sidebarToggle"><i class="el-icon-menu"></i></span>
        <div class="right">
                  <span class="header-btn">
                      <el-badge :value="3" class="badge">
                          <i class="el-icon-message"></i>
                      </el-badge>
                  </span>
          <span class="header-btn">
                      <i class="el-icon-bell"></i>
                  </span>
          <el-dropdown>
                      <span class="header-btn">
                          Admin<i class="el-icon-arrow-down el-icon--right"></i>
                      </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人中心</el-dropdown-item>
              <el-dropdown-item @click.native="logout">退出系统</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </div>
    </header>
    <LeftMenu :collapse="collapse"></LeftMenu>
  </div>
</template>
<style lang="less">
.sidebar-hidden {
    .header {
      .logo {
        .big {
          display: none;
        }
        .min {
          display: block;
        }
        width: 64px;
      }
    }

    .app-body {
      margin-left: 80px,
    }
  }
</style>
<script type="ts">
import "./header.less";
import LeftMenu from '../aside/aside';
export default {
  components: {
    LeftMenu
  },
  data() {
    return {
      collapse: false,
      site: {
        name: "Egg + TypeScript + Webpack",
        description: "Egg"
      }
    };
  },
  computed: {},
  methods: {
    sidebarToggle(e) {
      e.preventDefault();
      if (this.collapse) {
        document.body.classList.remove("sidebar-hidden");
        this.siteName = "Egg";
        this.collapse = false;
      } else {
        document.body.classList.add("sidebar-hidden");
        this.collapse = true;
      }
    },
    logout() {
      window.location.replace('/login');
    }
  },
  mounted: function() {
    if (!this.collapse) {
      document.body.classList.remove("sidebar-hidden");
      this.siteName = "Egg + TypeScript + Webpack";
    } else {
      document.body.classList.add("sidebar-hidden");
    }
  }
};
</script>
