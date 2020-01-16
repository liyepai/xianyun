<template>
  <div class="herder">
    <!-- 左边 -->
    <el-row type="flex" justify="space-between" align="middle" class="left">
      <img src="logo.jpg" alt="" />

      <el-row type="flex" class="daohan">
        <nuxt-link to="/">首页</nuxt-link>
        <nuxt-link to="./post">旅游攻略</nuxt-link>
        <nuxt-link to="./hotel">酒店</nuxt-link>
        <nuxt-link to="./air">国内机票</nuxt-link>
      </el-row>

      <!-- 右边 -->
      <div class="right">
        <nuxt-link to="/user/login">登录/注册</nuxt-link>
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
  box-shadow: 0 3px 0 #f5f5f5;
}
.left {
  display: flex;
  img {
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

      &:hover {
        color: #409eff;
        border-bottom: 5px solid #409eff;
      }
    }
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
