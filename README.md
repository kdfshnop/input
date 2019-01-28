# vue中input正则校验
```
<template>
  <div :class="'el-input el-input--small' + (disabled ? ' is-disabled' : '')">
    <input :placeholder="placeholder" :disabled="disabled" class="el-input__inner" type="text" ref="input" :value="value" v-on:input="changeInput($event.target.value)" v-on:change="changeInput($event.target.value)">
  </div>
</template>
<script>
export default {
  props: {
    reg: String,
    value: '',
    disabled: Boolean,
    placeholder: String
  },
  methods: {
    changeInput(val) {
      if (!this.reg) return this.$emit('input', val)
      let regexp = new RegExp(this.reg)
      let a = regexp.exec(val)
      this.$refs.input.value = a[0]
      this.$emit('input', a[0])
    }
  }
}
</script>
```