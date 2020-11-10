<template>
  <div>
    <el-container>
      <el-header>
        <p>我的名字是：{{ name }}</p>
      </el-header>
      <el-main>
        <h1>{{ profile }}</h1>
        <el-row>
          <el-button>默认按钮</el-button>
          <el-button type="primary" @click="pop">主要按钮</el-button>
          <el-button type="success" @click="tip">成功按钮</el-button>
          <el-button type="info" @click="login">信息按钮</el-button>
          <el-button type="warning">警告按钮</el-button>
          <el-button type="danger">危险按钮</el-button>
        </el-row>
      </el-main>
      <el-footer>
        <el-input v-model.number="numberA" placeholder="请输入内容"></el-input>
        <span> + </span>
        <el-input v-model.number="numberB" placeholder="请输入内容"></el-input>
        <span> = </span>
        <el-input v-model.number="computedResult" :disabled="true"></el-input>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import oidc from 'oidc-client'

export default {
  data () {
    return {
      name: null,
      numberA: '',
      numberB: '',
      config: {
        authority: 'https://localhost:44370',
        client_id: 'Js_App',
        redirect_uri: 'https://localhost:5003/callback.html',
        response_type: 'code',
        scope: 'openid profile BookStore',
        post_logout_redirect_uri: 'https://localhost:5003/index.html'
      },
      profile: ''
    }
  },
  computed: {
    computedResult: function () {
      return this.numberA + this.numberB
    }
  },
  created () {
    // this.name = this.$route.query.name
  },
  mounted () {
    this.name = this.$route.query.name
  },
  methods: {
    pop: function () {
      alert('hello')
    },
    close: function () {
      alert('close')
    },
    tip () {
      this.$message({
        message: '恭喜你，这是一条成功消息',
        type: 'success',
        showClose: true
      })
    },
    login () {
      var mgr = new oidc.UserManager(this.config)

      mgr.getUser().then(function (user) {
        if (user) {
          this.profile = user.profile
        } else {
          this.profile = 'User not logged in'
        }
      })
    }
  }
}
</script>

<style scoped>
  p{
    display: block;
    margin: 0;
  }
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  body > .el-container {
    margin-bottom: 40px;
  }
  .el-input {
    width: 70px;
  }
</style>
