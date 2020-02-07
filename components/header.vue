<template>
  <div class="herder">
    <!-- 左边 align="middle"垂直   justify="space-between" 左右贴边-->
    <el-row type="flex" justify="space-between" align="middle" class="left">
      <img src="/logo.jpg" alt="" class="logo" />
      <!-- el-row type="flex" 这个是ui框架的  可以兼容低版本的ie浏览器 -->
      <el-row type="flex" class="daohan">
        <nuxt-link to="/">首页</nuxt-link>
        <nuxt-link to="/post">旅游攻略</nuxt-link>
        <nuxt-link to="/hotel">酒店</nuxt-link>
        <nuxt-link to="/air">国内机票</nuxt-link>
      </el-row>
      <!-- 右边 -->
      <div class="right">
        <nuxt-link to="/user/login" v-if="!$store.state.user.userInfo.token"
          >登录/注册</nuxt-link
        >
        <el-dropdown v-if="$store.state.user.userInfo.token">
          <span class="el-dropdown-link">
            <img
              :src="
                $axios.defaults.baseURL +
                  $store.state.user.userInfo.user.defaultAvatar
              "
              alt=""
              class="imgg"
              width="36px"
              height="36px"
            />
            {{ $store.state.user.userInfo.user.nickname }}
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>个人中心</el-dropdown-item>
            <el-dropdown-item>退出</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </el-row>
  </div>
</template>

<script>
export default {};
</script>

<style socped lang="less">
.herder {
  width: 1000px;
  height: 60px;
  align-items: center;
  margin: 0 auto;
  // 阴影
  box-shadow: 0 3px 0 #f5f5f5;
}
.left {
  display: flex;
  .logo {
    display: block;
    width: 156px;
    height: 42px;
    margin: auto 0;
  }
  .daohan {
    flex: 1;
    a {
      display: block;
      height: 60px;
      line-height: 60px;
      padding: 0 20px;
      // &:hover  相当： a:hover
      &:hover {
        color: #409eff;
        border-bottom: 5px solid #409eff;
      }
    }
    // .nuxt-link-exact-active 框架给我们当前路由的  一个类  可做扩展
    .nuxt-link-exact-active {
      color: #fff;
      background-color: #409eff;
      &:hover {
        color: #fff;
      }
    }
  }
}
</style>
