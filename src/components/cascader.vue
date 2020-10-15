<template>
  <div>
    <Popover>
      <template>
        <div class="options">
          
        </div>
      </template>
      <div slot="reference">
        <my-select></my-select>
      </div>
    </Popover>
  </div>
</template>

<script>
import Popover from './popover'
import mySelect from './select'
export default {
  name: 'Cascader',
  props: {
    options:{
      type: Array
    }
  },
  components: { 
    mySelect,
    Popover
  },
  data () {
    return {

    }
  },
  methods: {
    handlefocus () {
      console.log('lsdkfja;')
    },
    handleblur () {
      console.log('jjdjj')
    }
  }
}
</script>

<style>

</style>
