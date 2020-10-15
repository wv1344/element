<template>
  <Popover :width="100">
    <template>
      <slot></slot>
    </template>
      <div slot="reference" class="select-content">
        <input
          class="select-source"
          v-model="innerValue"
          :placeholder="placeholder"
          @input="handleInput"
          @focus="handleFocus"
          @blur="handleBlur"
          :disabled="disabled"
        />
        <span class="clear" v-if="clearShow" @click="clearInput">
          <i class="iconfont iconziyuanxhdpi"></i>
        </span>
        <span class="select-suffix">
          <slot name="suffix"></slot>
        </span>
      </div>
  </Popover>
</template>

<script>
import Popover from './popover'
export default {
  name: 'Select',
  props: {
    type: {
      type: String,
      default: 'text'
    },
    value: [String, Number],
    placeholder: {
      type: String,
      default: '请输入内容'
    },
    clearable: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  components: {
    Popover
  },
  data () {
    return {
      clearShow: false,
      innerValue: this.value,
      showSelect: false
    }
  },
  created () {
    if (this.value && this.clearable) {
      this.clearShow = true
    }
  },

  methods: {
    handleInput (val) {
      this.$emit('input', val.target.value)
    },
    handleFocus (val) {
      this.showSelect = true
      this.$emit('focus', val)
    },
    handleBlur (val) {
      this.showSelect = false
      this.$emit('blur', val)
    },
    clearInput () {
      event.stopPropagation()
      this.innerValue = ''
      this.$emit('input', '')
    }
  },
  watch: {
    innerValue () {
      if (!this.innerValue) {
        this.clearShow = false
      } else {
        this.clearShow = true
      }
    },
    value (newVal) {
      this.innerValue = newVal
    }
  }
}
</script>
<style lang='stylus' scoped>
.select-content
  display: inline-block;
  position: relative;
  cursor pointer
  .select-source
    font-size: 16px;
    height: 36px;
    line-height: 40px;
    border: 1px solid #dcdfe6;
    border-radius: 4px;
    padding: 0 30px 0 15px;
    outline: none;
    font-size 14px
    color #333
    cursor pointer
  .select-source:focus
    border-color: #409eff;

  .select-source:disabled
    background-color: #f5f7fa;
    color: #c0c4cc;
    cursor: not-allowed;

  .clear
    display: none;
    cursor: pointer;

.select-content:hover .clear
  display: block;
  position: absolute;
  top: 10px;
  right: 10px;
  color: #ccc;

.select-suffix
  position absolute
  right 8px
  top 50%
  transform translateY(-50%)
</style>
