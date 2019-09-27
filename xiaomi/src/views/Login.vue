<template>

	<div class="login">

		<div class="loheader">
			<em class="logo"></em>
			<h3 class="logo-title" style="color: #828282;">小米账号服务</h3>
		</div>
		<div class="deng">
			<div class="deng-top">
				+86 > <input ref="phone" type="text" placeholder="请输入手机号" /><!-- @keyup="pho" -->
			</div>
			<div class="deng-bom"><input ref="code" type="text" placeholder="短信验证码" /><span @click="sendCode" style="color: #ff6700;">获取验证码</span></div>
		</div>
		
		<!-- <span id="hut" style="display: none;">请输入手机号码！</span> -->
		<input ref="pho" type="text" style="display: none;" placeholder="请输入手机号" />
		
		<div class="denglu">
			
			<h3 @click="login">立即登录注册</h3>
		</div>
		<div class="denglu2">
			<h3 @click="toLog" style="color: #828282;">用户名密码登录</h3>
		</div>
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
		name: "Login",
		
		
		methods: {
			
			sendCode() {
				let ab = this.$refs.phone.value
				if (ab.length == 11) {
					let phoneReg = /^[1][3,4,5,7,8][0-9]{9}$/;
					if (!phoneReg.test(ab)) {
						alert('手机号码输入有误')
					} else {
						axios.post('/user/sendVerifyCode', {
							phone: this.$refs.phone.value
						}).then((result) => {
							alert('已经发送');
						}).catch(console.error)
					}
				} else {
					alert('手机号码输入有误')
				}

			},

			toLog() {
				this.$router.push({
					name: 'log'
				})
			},


			login() {
				let ab = this.$refs.phone.value
				let code = this.$refs.code.value
				
				if (ab === '') {
					alert('请输入手机号码')
				} else if(ab.length == 11){
					let phoneReg = /^[1][3,4,5,7,8][0-9]{9}$/;
					if (!phoneReg.test(ab)) {
						
						sho.style.display = 'block'
						alert('手机号码输入有误')	
					}else if(code == ''){
						alert('请输入验证码')
					}else{
						// sho.style.display = 'none'
						axios.post('/user/loginByCode', {
						phone: this.$refs.phone.value,
						code: this.$refs.code.value,
						
					}).then((result) => {
						console.log(result.data);
						this.$router.back()
						
					}).catch(console.error)
					}
				// }else{
				// 	alert('请您规范填写')
				 }

			},
			
		}
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
		border: solid 1px #ff6700;
		margin-top: 60px;
		border-radius: 12px;
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
