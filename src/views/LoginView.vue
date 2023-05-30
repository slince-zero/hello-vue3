<template>
  <div class="login-container">
    <div class="login-content">
      <el-form
        ref="formRef"
        :model="form"
        :rules="rules"
        label-width="auto"
        hide-required-asterisk="false"
      >
        <el-form-item label="用户名" prop="name" style="color: brown">
          <el-input v-model="form.name" />
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input v-model="form.password" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit(formRef)">login</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'
import { FormInstance } from 'element-plus'
const form = ref({
  name: '',
  password: '',
})

const formRef = ref<FormInstance>()
const rules = reactive({
  name: [{ required: true, message: '请输入用户名', trigger: 'blur' }],
  password: [{ required: true, message: '请输入密码', trigger: 'blur' }],
})

const onSubmit = (form: FormInstance) => {
  form.validate((valid, fileds) => {
    if (valid) {
      console.log('登录成功')
    } else {
      console.log('登录失败', fileds)
    }
  })
}
</script>

<style>
.login-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background: url('../assets/bgc.jpg');
}
.login-content {
  height: 300px;
  width: 400px;
  border-radius: 5px;
  /* background-color: grey; */
  backdrop-filter: blur(15px);
}
.el-form {
  margin-top: 80px;
}
.el-button {
  width: 100%;
  margin: 10px 0 0 55px;
}
.el-form-item__label {
  color: #d1dbe5;
}
</style>
