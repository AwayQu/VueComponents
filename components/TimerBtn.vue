<template>
    <el-button @click="handleClick"
            :disabled="disabled || time > 0">
        {{ text }}
    </el-button>
</template>
<script>
  import ElButton from "../../node_modules/element-ui/packages/button/src/button";
  export default {
    components: {ElButton},
    name: 'TimerBtn',
    componentName: 'TimerBtn',
    props: {
      second: {
        type: Number,
        default: 60
      },
      disabled: {
        type: Boolean,
        default: false
      }
    },
    data: function () {
      var time = sessionStorage.getItem('time') ? sessionStorage.getItem('time') : 0;
      if (time > 0) {
        this.run();
      }
      return {
        time: time
      }
    },
    methods: {
      run: function () {
        this.time = this.second;
        sessionStorage.setItem('time', this.time);
        this.timer()
      },
      timer: function () {
        if (this.time > 0) {
          this.time--;
          sessionStorage.setItem('time', this.time);
          setTimeout(this.timer, 1000);
        }
      },
      handleClick: function(evt) {
        this.$emit('click', evt);
      }
    },
    computed: {
      text: function () {
        return this.time > 0 ? this.time + 's 后重新获取' : '获取验证码';
      }
    },
  }
</script>