<template>
<div>
  <h1>{{ msg }}</h1>
  <el-input v-model="input" placeholder="请输入内容"></el-input> <span>+</span> <input v-model.number="b" @change="compute"> <span>=</span> <input v-model.number="result">
</div>
</template>

<script>
export default {
  name: 'Demo',
  data () {
    return {
      msg: 'My Demo!',
      value: 0,
      a: 0,
      b: 0
    }
  },
  computed: {
    result: function () {
      return this.a + this.b
    }
  },
  methods: {
    compute: function () {
      this.result = this.a + this.b
    }
  }
}
</script>
