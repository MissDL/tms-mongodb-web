<template>
  <div class="login">
    <tms-login :on-success="fnSuccessToken" class="tms-login"></tms-login>
  </div>
</template>
<script>
export default {
  methods: {
    fnSuccessToken(newToken) {
      window.sessionStorage.setItem('access_token', newToken)
      if (this.$tmsRouterHistory.canBack()) {
        this.$router.back()
      } else {
        this.$router.push({name: 'home'})
      }
    }
  }
}
</script>
<style lang="less" scoped>
.login {
  display: flex;
  justify-content: center;
  margin-top: 200px;
	/* transform: translate(-50%, -50%); */
	
	.tms-login {
		border: 1px solid #ddd;
	}
}
</style>