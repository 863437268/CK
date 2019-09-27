<template>
	
    <div class="login">
       
		<div class="loheader">
			<em class="logo"></em>
			<h3 class="logo-title" style="color: #828282;">注册小米账号</h3>
		</div>
		<div class="deng">
			 <div class="deng-top">
				 <input ref="phone" type="text" placeholder="中国"/>
			</div> 
			<!-- +86 > <input ref="phone" type="text" placeholder="请输入手机号" /> -->
			<div class="deng-bom">+86  ><input ref="phone" type="text" placeholder="请输入手机号码"/><!-- <button @click="sendCode">获取验证码</button> --></div>
			<div class="duan-xin"><input ref="code" type="text" placeholder="短信验证码" /><span @click="sendCode" style="color: #ff6700;">获取验证码</span></div>
			<div class="pwd"><input ref="pwd" type="password" placeholder="请输入密码" /><!-- <button @click="send">口</button> --></div>
		</div>
       
        <div class="dl"><h3 @click="logo">注册登录</h3></div>
		
		<ul class="dibu">
		<li>简体</li>
		<li>|</li>
		<li>繁体</li>
		<li>|</li>
		<li>English</li>
		<li>|</li>
		<li>常见问题</li>
		
	</ul>
    </div>
	
</template>

<script>
    import axios from 'axios';
    export default {
        name: "zhuce",
		
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
			
			 logo() {
				 let ac = this.$refs.pwd.value
				 if(!ac == ''){
					 let pwdReg = /^[0-9A-Za-z]{8,16}$/;
					 if (!pwdReg.test(ac)) {
					 	alert('请输入由8-16位数字或这字母组成密码')
					 } else {
					 
					 
					 axios.post('/user/loginByCode', {
			        phone: this.$refs.phone.value,
			        code: this.$refs.code.value,
					pwd: this.$refs.pwd.value,
			    }).then((result) => {
					alert('恭喜注册登录成功')
			        console.log(result.data);
			        // this.$router.back();
					this.$router.push({
						name: 'user'
					})
			    }).catch(console.error) 
				}
				
				 // }else{
					//  alert('请输入账号和密码')
				 // }
			   
			}else{
					alert('请输入正确手机号和密码')
				}
	
  

			 
        }
    },
	}
</script>

<style scoped>
	.login{
		width: 100%;
	}
	
.loheader{
	height: 200px;
	margin: 0 auto;
	padding: 60px 0 20px;
}

.logo{
	width: 96px;
    height: 96px;
    margin: 0 auto 30px;
    display: block;
	 background: url(../images/milogo@2x.png);
}

.logo-title{
	font-size: .36rem;
	text-align: center;
}

.deng{
	height: 218px;
	width: 90%;
	margin-left: .4rem;
}

.deng-top{
	width: 90%;
	margin-left: .4rem;
	line-height: 108px;
	text-align: center;
	border-bottom: 1px solid #ff6700;
}

.deng-bom{
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
		 border:none;
		outline: none;   
    }
	.dl{
		width: 90%;
		margin-left: .4rem;
		margin-top: 3rem; 
		text-align: center;
		line-height: .88rem;
		background: #ff6700;
		border: solid 1px;
		border-radius: 12px; 
	}
	.dl>h3 {
		background:#ff6700; 
			/* padding: 10px; */
			color: white
		}
	.duan-xin{
		 width: 100%;
		margin-top: 40px;
		text-align: center;
		line-height: 88px;
		/* background: #ff6700; */
		border: solid 1px #ff6700;
		border-radius: 12px; 
	}
	.pwd{
		 width: 100%;
		margin-top: 40px;
		text-align: center;
		line-height: 88px;
		/* background: #ff6700; */
		border: solid 1px #ff6700;
		border-radius: 12px; 
	}
	.dibu{
		width: 7.2rem;
		list-style: none;
		padding-left: .5rem;
	}
	.dibu>li{ 
		float: left;
		margin-top: 2rem;
		text-align: center;
		padding: 0 .2rem;
		color:#828282;
		font-size: .3rem;
	}
</style>
