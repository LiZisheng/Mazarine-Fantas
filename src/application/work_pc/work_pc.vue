<template>
  <div id="app">
    <a-layout id="components-layout-demo-custom-trigger">
      <a-layout-sider :trigger="null" collapsible v-model="collapsed">
        <div class="logo" />
        <a-menu theme="dark" mode="inline" selectedKeys="[this.$route.path]">
          <a-menu-item key="/Home" >
            <router-link to="/Home">
              <a-icon type="user" />
              <span>nav 1</span>
            </router-link>
          </a-menu-item>
          <a-menu-item key="/Setting" >
            <router-link to="/Setting">
              <a-icon type="video-camera" />
              <span>nav 2</span>
            </router-link>
          </a-menu-item>
          <a-menu-item key="3" >
            <a-icon type="upload" />
            <span>nav 3</span>
          </a-menu-item>
        </a-menu>
      </a-layout-sider>
      <a-layout>
        <a-layout-header style="background: #fff; padding: 0">
          <a-icon
            class="trigger"
            :type="collapsed ? 'menu-unfold' : 'menu-fold'"
            @click="() => (collapsed = !collapsed)"
          />
          <a-button type="primary" href='login_pc'>Primary</a-button>
        </a-layout-header>
        <a-layout-content
          :style="{
            margin: '0px 16px',
          }"
        >
          <router-view></router-view>
        </a-layout-content>
        <a-layout-footer style="text-align: center">
        English Writing Platform ©2020 Created by Mazarine-Fantas
      </a-layout-footer>
      </a-layout>
    </a-layout>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'

function isPC() {
  //是否為PC端
  var userAgentInfo = navigator.userAgent;
  var Agents = [
    "Android",
    "iPhone",
    "SymbianOS",
    "Windows Phone",
    "iPad",
    "iPod"
  ];
  var flag = true;
  for (var v = 0; v < Agents.length; v++) {
    if (userAgentInfo.indexOf(Agents[v]) > 0) {
      flag = false;
      break;
    }
  }
  return flag;
}

export default {
  name: "App",
  data() {
    return {
      collapsed: false,
    };
  },
  created() {
    this.$router.push({ path: '/Home' });
    console.log("isPC");
    if (isPC() === true) {
      console.log("isPC = true");
    } else {
      document.location.href = "/work_mobile";
      console.log("isPC = false");
    }
  },
  methods: {
  }
};
</script>

<style>
#app {
  font-family: "SF Pro TC", "SF Pro Text", "SF Pro Icons", "PingFang TC",
    "Helvetica Neue", "Helvetica", "Arial", "Microsoft JhengHei", wf_SegoeUI,
    "Segoe UI", Segoe, "Segoe WP", Tahoma, Verdana, Ubuntu,
    "Bitstream Vera Sans", "DejaVu Sans", Tahoma, 微軟正黑體, "LiHei Pro",
    "WenQuanYi Micro Hei", "Droid Sans Fallback", "AR PL UMing TW", Roboto,
    "Helvetica Neue", "Hiragino Maru Gothic ProN", メイリオ,
    "ヒラギノ丸ゴ ProN W4", Meiryo, "Droid Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100%;
}

#components-layout-demo-custom-trigger {
  height: 100%;
}

#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #1890ff;
}

#components-layout-demo-custom-trigger .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
}
</style>
