<template>
  <div class="full-screen flex justify-center items-center">
    <el-card shadow="always" :body-style="{ padding: '20px', height: '250px', width: '450px' }">
      <div slot="header">
        <p class=" text-stroke-dark-50 text-stroke-sm text-5xl text-light-50 text-center">LOGIN</p>
      </div>
      <el-form :model="submitForm" ref="form" label-width="80px" :inline="false" size="default" class="ml-10"
        label-position="left">

        <!-- 名字选择框 -->
        <el-form-item label="名前" class="mt-6">
          <el-select v-model="submitForm.name" placeholder="Name" size="default" class=" !w-55">
            <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value" />
          </el-select>
        </el-form-item>

        <!-- 学号输入框 -->
        <el-form-item label="学生番号" class="mt-4">
          <el-input v-model="submitForm.number" placeholder="STUDENT NUMBER" size="default" clearable
            class=" !w-55"></el-input>
        </el-form-item>

        <el-form-item class="mt-5">
          <el-button type="primary" @click="SubmitForm" class="w-45">LOGIN</el-button>
        </el-form-item>
      </el-form>

      <!-- card body -->
    </el-card>

  </div>
</template>

<script setup>
import { reactive } from "vue"
import router from "@/router"

const submitForm = reactive({
  name: "",
  number: ""
})


// 前端进行身份认证
function SubmitForm() {
  options.forEach((e) => {
    if (e.value == submitForm.name && e.number == submitForm.number) {
      router.push("/about")
    }
  })
}

// 默认可以登入人员的名字和学号
const options = [
  {
    value: 'LIAO YUNFENG',
    label: 'LIAO YUNFENG',
    number: 'B2278562'
  },
  {
    value: 'Member1',
    label: 'Member1',
    number: 'number1'
  },
  {
    value: 'Member2',
    label: 'Member2',
    number: 'number2'
  },
  {
    value: 'Member3',
    label: 'Member3',
    number: 'number3'
  }
]
</script>