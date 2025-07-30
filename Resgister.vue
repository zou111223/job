<template>
  <el-form :model="form" label-width="80px" style="max-width:350px;margin:60px auto">
    <el-form-item label="用户名">
      <el-input v-model="form.username"/>
    </el-form-item>
    <el-form-item label="密码">
      <el-input type="password" v-model="form.password"/>
    </el-form-item>
    <el-form-item label="手机号">
      <el-input v-model="form.phone"/>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="register">注册</el-button>
      <el-button link @click="toLogin">登录</el-button>
    </el-form-item>
  </el-form>
</template>
<script setup>
import { ref } from 'vue'
import { register } from '../api/user'
import { useRouter } from 'vue-router'
const form = ref({ username:'', password:'', phone:'' })
const router = useRouter()
async function registerHandler() {
  await register(form.value)
  router.push('/login')
}
function toLogin() {
  router.push('/login')
}
const register = registerHandler
</script>
