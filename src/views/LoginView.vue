<template>
  <div class="login-wrap">
    <div class="ms-login">
      <div class="ms-title">后台管理系统</div>
      <el-form
        ref="formRef"
        :model="form"
        :rules="rules"
        label-width="0px"
        class="ms-content"
        hide-required-asterisk="false"
      >
        <el-form-item prop="name" style="color: brown">
          <el-input v-model="form.name">
            <template #prepend>
              <el-button :icon="User"></el-button>
            </template>
          </el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input type="password" v-model="form.password">
            <template #prepend>
              <el-button :icon="Lock"></el-button>
            </template>
          </el-input>
        </el-form-item>
        <el-form-item class="login-btn">
          <el-button type="primary" @click="onSubmit(formRef)">login</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'
import { FormInstance } from 'element-plus'
import router from '@/router'
import { ElMessage } from 'element-plus'
import { Lock, User } from '@element-plus/icons-vue'
const form = ref({
  name: 'admin',
  password: '123456',
})

const formRef = ref<FormInstance>()
const rules = reactive({
  name: [{ required: true, message: '请输入用户名', trigger: 'blur' }],
  password: [{ required: true, message: '请输入密码', trigger: 'blur' }],
})

const open = () => {
  ElMessage({
    message: '登录成功',
    grouping: true,
    type: 'success',
    duration: 1000,
  })
}

const onSubmit = (formEl: FormInstance) => {
  console.log(formRef.value)

  formEl.validate((valid, fileds) => {
    if (!valid) return

    if (valid) {
      console.log(form.value.name)
      router.push('/home')
      open()
    } else {
      console.log('登录失败', fileds)
    }
  })
}
</script>

<style scoped>
.login-wrap {
  position: relative;
  width: 100%;
  height: 100%;
  background: url(../assets/bgc.jpg);
  /* background-size: 100%; */
}

.ms-title {
  width: 100%;
  line-height: 50px;
  text-align: center;
  font-size: 20px;
  color: #fff;
  border-bottom: 1px solid #ddd;
}
.ms-login {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 350px;
  margin: -190px 0 0 -175px;
  border-radius: 5px;
  background: rgba(255, 255, 255, 0.3);
  overflow: hidden;
}
.ms-content {
  padding: 30px 30px;
}
.login-btn {
  text-align: center;
}
.login-btn button {
  width: 100%;
  height: 36px;
  margin-bottom: 10px;
}
</style>
