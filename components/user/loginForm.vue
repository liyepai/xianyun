<template>
  <el-form :model="user" status-icon :rules="rules" ref="form" class="form">
    <el-form-item label="用户名:" prop="username">
      <el-input v-model="user.username" placeholder="用户名/手机"></el-input>
    </el-form-item>
    <el-form-item label="密码:" prop="password">
      <el-input
        type="password"
        v-model="user.password"
        placeholder="请输入密码"
      ></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="denglu">登录</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  data() {
    const nameguize = (rule, value, callback) => {
      if (!value) {
        callback(new Error("请输入用户名"));
      } else if (!/^1[3-9][0-9]{9}$/.test(value)) {
        callback(new Error("请输入正确格式用户名"));
      } else {
        callback();
      }
    };
    return {
      user: {
        username: "",
        password: ""
      },
      rules: {
        username: [
          {
            validator: nameguize,
            trigger: "blur"
          }
        ],
        password: [
          {
            required: true,
            message: "请输入密码",
            trigger: "blur"
          },
          {
            min: 3,
            max: 16,
            message: "请输入3-16位密码",
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    denglu() {
      this.$refs["form"].validate(valid => {
        if (valid) {
          this.$axios({
            method: "post",
            url: "/accounts/login",
            data: this.user
          }).then(res => {
            const data = res.data;
            // 保存到state
            //传给仓库
            this.$store.commit("user/setUserInfo", data);
          });
        } else {
          this.$message.error("输入格式不正确");
        }
      });
    }
  }
};
</script>

<style scoped lang="less">
.form {
  padding: 25px;
}

.form-item {
  margin-bottom: 20px;
}

.form-text {
  font-size: 12px;
  color: #409eff;
  text-align: right;
  line-height: 1;
}

.submit {
  width: 100%;
  margin-top: 10px;
}
</style>
