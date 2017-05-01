# VueComponents

* 倒计时验证码按钮,防浏览器刷新

## Components

### 1.TimerBtn.vue
  
  
### usage
```html
  <el-form-item prop="securityCode">
            <el-input style="width: 62%" type="text" v-model="ruleForm2.securityCode" auto-complete="off" placeholder="验证码"></el-input>
            <timer-btn type="primary" style="width: 36%; float: right" class="btn btn-default" @click="send" ref="btn"></timer-btn>
        </el-form-item>
  
```

```Javascript

<script>
  import TimerBtn from "../components/TimerBtn";

  export default {
    components: {TimerBtn},
    data() {
      return {
    },
    methods: {
      send: function () {
        this.$message({
          message: "send",
          type: 'success'
        });
        this.$refs.btn.disabled = true;
        setTimeout(this.sended, 2000);
      },
      sended() {
        this.$refs.btn.run();
        this.$refs.btn.disabled = false;
      }
    }
  }

</script>
```
