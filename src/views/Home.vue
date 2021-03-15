<template>
  <div class="home">
    <el-card class="menu-container" shadow="hover">
      <div slot="header" class="clearfix">
        <span><h2>Menu</h2></span>
      </div>
      <div class="option-container">
        <el-button class="btn-ops" type="primary" plain @click="redirectPage" v-loading.fullscreen.lock="fullscreenLoading">Start</el-button>
        <el-button class="btn-ops" type="danger" plain style="margin-top: 10px">End</el-button>
      </div>
    </el-card>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data () {
    return {
      fullscreenLoading: false
    }
  },
  methods: {
    redirectPage () {
      this.fullscreenLoading = true
      setTimeout(() => {
        this.$router.push('Dashboard')
      }, 3000)
    }
  }
}
</script>
<style>
  .menu-container {
    margin: 0 auto;
    width: 600px;
  }
  .option-container {
    display: grid;
  }
  .btn-ops {
    display: block;
    margin-left: 0px !important;
  }
</style>
