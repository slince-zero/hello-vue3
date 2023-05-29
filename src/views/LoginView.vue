<template>
  <div>
    <el-form :model="form" :rules="rules" label-width="120px">
      <el-form-item label="用户名" prop="form.name">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="密码" prop="form.password">
        <el-input v-model="form.password" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">Create</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'
const form = ref({
  name: '',
  password: '',
})

const rules = reactive({
  name: [
    { required: true, message: 'Please input Activity name', trigger: 'blur' },
  ],
  password: [
    { required: true, message: 'Please input Activity name', trigger: 'blur' },
  ],
})

const onSubmit = () => {
  console.log('submit')
}
</script>

<style></style>
