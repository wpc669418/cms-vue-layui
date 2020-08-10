<template>
  <div id="app">
    <div class="layui-container">
      <form class="layui-form layui-form-pane" action="">
        <div class="layui-form-item">
          <label class="layui-form-label">用户名</label>
          <div class="layui-input-block">
            <input
              type="text"
              name="title"
              required
              lay-verify="required"
              placeholder="请输入用户名"
              autocomplete="off"
              class="layui-input"
            />
          </div>
        </div>
        <div class="layui-form-item">
          <label class="layui-form-label">密码</label>
          <div class="layui-input-block">
            <input
              type="password"
              name="title"
              required
              lay-verify="required"
              placeholder="请输入密码"
              autocomplete="off"
              class="layui-input"
            />
          </div>
        </div>
        <div class="layui-form-item">
          <label class="layui-form-label">验证码</label>
          <div class="layui-input-inline">
            <input
              name="password"
              required
              lay-verify="required"
              placeholder="请输入图形验证码"
              autocomplete="off"
              class="layui-input"
            />
          </div>
          <div class="layui-form-mid layui-word-aux captcha-div" v-html="captcha">辅助文字</div>
        </div>
        <div class="layui-form-item">
          <div class="layui-input-block">
            <button class="layui-btn" lay-submit lay-filter="formDemo">
              立即提交
            </button>
            <a href="#" class="forget-btn">
              忘记密码？
            </a>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'app',
  data () {
    return {
      captcha: ''
    }
  },
  mounted () {
    axios.get('http://localhost:3000/user/getCaptcha', {
      params: {
        key: 123
      }
    }).then(res => {
      console.log('mounted -> res', res)
      this.captcha = res.data.data
    })
  }
}
</script>

<style lang="scss" scoped>
#app {
  background: #f2f2f2;
}
.layui-container {
  background: #ffffff;
}
.forget-btn {
  margin-left: 10px;
  &:hover {
    color: #009688;
  }
}
input {
  width: 190px;
}
.captcha-div{
  position: relative;
  top: -15px;
}
</style>
