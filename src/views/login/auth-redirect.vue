<template>
  <div class="forget-password">
    <el-button
      style="margin: 12px"
      size="small"
      type="plain"
      @click="back"
    >返回登录</el-button>
    <div style="width: 70%; margin: 20px auto">
      <h2>忘记密码</h2>
      <el-row style="width: 100%; padding-top: 55px; position: relative">
        <el-steps :active="active" style="padding: 55x 0">
          <el-step title="第1步" icon="el-icon-success" />
          <el-step title="第2步" icon="el-icon-success" />
          <el-step title="已完成" icon="el-icon-success" />
        </el-steps>
        <div v-if="active === 1" class="forget-form">
          <el-form ref="form" :model="form" label-width="10px" size="large">
            <el-form-item label="">
              <el-input
                v-model="form.name"
                prefix-icon="el-icon-user"
                placeholder="请输入账号"
              />
            </el-form-item>
            <el-form-item label="">
              <el-input
                v-model="form.email"
                prefix-icon="el-icon-message"
                placeholder="请输入验证邮箱"
              />
            </el-form-item>
            <el-form-item label="">
              <el-input
                v-model="form.code"
                prefix-icon="el-icon-circle-check"
                placeholder="请输入邮箱验证码"
                style="width: 250px; float: left"
              />
              <el-button type="primary">发送邮箱验证码</el-button>
            </el-form-item>
          </el-form>
        </div>
        <el-button
          type="primary"
          class="next-btn"
          size="large"
          @click="next"
        >下一步</el-button>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      active: 1,
      form: {
        name: '',
        email: '',
        code: ''
      }
    }
  },
  methods: {
    back() {
      this.$router.go(-1)
    },
    next() {
      if (this.active++ > 2) this.active = 0
    }
  }
}
</script>

<style lang="scss" scoped>
.m50 {
  margin: 50px;
}
.forget-form {
  width: 400px;
  text-align: center;
  margin: 60px auto;
}
.next-btn {
  width: 120px;
  position: absolute;
  left: 50%;
  margin-left: -60px;
}
</style>
