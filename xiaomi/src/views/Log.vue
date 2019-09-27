<template>

	<div class="login">

		<div class="loheader">
			<em class="logo"></em>
			<h3 class="logo-title" style="color: #828282;">小米账号登录</h3>
		</div>
		<div class="deng">
			<div class="deng-top">
				<input ref="phone" type="text" placeholder="邮箱/手机号码/小米ID" />
			</div>
			<div class="deng-bom"><input ref="pwd" type="password" placeholder="密码" /><!-- <button @click="sendCode">获取验证码</button> -->
			</div>
		</div>

		<div class="denglu">
			<h3 @click="logo">登录</h3>
		</div>
		<div class="denglu2">
			<h3 @click="log" style="color: #797676">手机短信登录/注册</h3>
		</div>
		<div class="forget"><span @click="register">立即注册</span> | <span @click="forg">忘记密码</span></div>
		<div class="qita">
			<p>其他方式登录</p>
		</div>
		<div class="qita-dl">
			<a><img src="../images/xinlang.png"></a>
			<a><img src="../images/zhifubao.png"></a>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	export default {
		// data() {
		// 	return {
		// 		isLogin: existCookie('token')
		// 	}
		// },
		
		name: "Log",
		methods: {
			
			log() {
				let ab = this.$refs.phone.value
				if (ab == '') {
					axios.post('/user/loginByCode', {
						phone: this.$refs.phone.value,
						pwd: this.$refs.pwd.value,

					}).then((result) => {

						console.log(result.data);
						this.$router.back();
					}).catch(console.error)
				}

			},
			logo() {
				let phone = this.$refs.phone.value
				let pwd = this.$refs.pwd.value
				if (!(phone && pwd == existCookie('token'))) {
					axios.post('/user/loginByCode', {
						phone: this.$refs.phone.value,
						pwd: this.$refs.pwd.value,

					}).then((result) => {
						alert('暂无此账号')
						console.log(result.data);
						this.$router.go()

					}).catch(console.error)
				} else {
					alert('登录成功')
					this.$router.push({
						name: 'user'
					})
				}
			},
			register() {
				this.$router.push({
					name: 'zhuce'
				})
			},
			forg() {
				this.$router.push({
					name: 'zhuce'
				})
			},

			

		}
	}
	function existCookie(name) {
				let parts = document.cookie.split('; ');
				for (let part of parts) {
					if (name === part.split('=')[0]) {
						return true
					}
				}
				return false;
			}
</script>

<style scoped>
	.login {
		width: 100%;
	}

	.loheader {
		height: 200px;
		margin: 0 auto;
		padding: 60px 0 20px;
	}

	.logo {
		width: 96px;
		height: 96px;
		margin: 0 auto 30px;
		display: block;
		background: url(../images/milogo@2x.png);
	}

	.logo-title {
		font-size: .36rem;
		text-align: center;
	}

	.deng {
		height: 218px;
	}

	.deng-top {
		width: 90%;
		margin-left: .4rem;
		line-height: 108px;
		text-align: center;
		border-bottom: 1px solid #ff6700;
	}

	.deng-bom {
		width: 90%;
		margin-left: .4rem;
		line-height: 108px;
		text-align: center;
		border-bottom: 1px solid #ff6700;
	}

	.login {
		/* font-size: 0.5rem; */
	}

	.login * {
		font-size: .36rem;
	}

	input {
		/* border: 1px red solid; */
		border: none;
		outline: none;
	}

	.denglu {
		width: 90%;
		margin-left: .4rem;
		margin-top: 40px;
		text-align: center;
		line-height: 88px;
		background: #ff6700;
		border: solid 1px;
		border-radius: 12px;
	}

	.denglu>h3 {
		background: #ff6700;
		/* padding: 10px; */
		color: white
	}

	.denglu2 {
		width: 90%;
		margin-left: .4rem;
		text-align: center;
		line-height: 88px;
		border: solid 1px;
		margin-top: 60px;
		border-radius: 12px;
	}

	.forget {
		padding-top: .2rem;
		padding-left: 2rem;
	}

	.qita {
		padding-top: 100px;
		text-align: center;
	}

	.qita>p {
		font-size: 30px;
	}

	.qita-dl {
		text-align: center;
		padding-top: 60px;
	}

	.qita-dl>a {
		padding: 0 20px;
	}

	.qita-dl>a>img {
		width: 70px;
		height: 70px;
	}
</style>
