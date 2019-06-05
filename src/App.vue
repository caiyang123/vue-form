<template>
  <div id="app">
    <k-form :model="ruleForm" :rules="rules" ref="loginForm">
      <k-form-item label="用户名" prop="name">
        <k-input v-model="ruleForm.name"></k-input>
      </k-form-item>
      <k-form-item label="密码" prop="pwd">
        <k-input v-model="ruleForm.pwd"></k-input>
      </k-form-item>
      <k-form-item>
        <el-button type="primary" @click="onSubmit">提交</el-button>
      </k-form-item>
    </k-form>
  </div>
</template>

<script>
import KInput from "./components/KInput.vue";
import KFormItem from "./components/KFormItem.vue";
import KForm from "./components/KForm.vue";
export default {
  name: "app",
  components: {
    KInput,
    KFormItem,
    KForm
  },
  data() {
    return {
      ruleForm: {
        name: "",
        pwd: ""
      },
      rules: {
        name: [{ required: true, message: "姓名必填" },{ min: 3, max: 8, message: "姓名长度为3-8" }],
        pwd: [{ min: 4, max: 9, message: "密码长度为4-9" }]
      }
    };
  },
  methods: {
    onSubmit() {
      this.$refs.loginForm.validate(res => {
        if (res) {
          console.log("校验通过");
        } else {
          console.log("校验失败");
        }
      })
    }
  }
};
</script>

<style>
</style>
