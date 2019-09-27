<template>
	<div>
		<!--    个人中心 -->
		<div class="toubu">
			<div class="lg">
				<img src="../images/avatar.76a75b8f17.png" />
			</div>
			<!-- <div v-if="isLogin"> <img src="../images/微信图片_20190917210753.jpg"></div> -->
			<div v-if="isLogin" class="lg-hu">
				欢迎 大王回来
			</div>
			<div v-else class="dlu">
				<p @click="toLogin">登录注册</p>
				<!-- <van-button @click="toLogin">登录注册</van-button> -->
			
			</div>

		</div>
		<div class="dingdan">
			<span class="wode">我的订单</span>
			<span class="quanbu" @click="dingdan">全部订单 &nbsp;&nbsp;<img src="../images/QQ截图20190924165926.png"></span>
		</div>
		<div class="serve">
			<ul class="serve-ul">
				<li><img src="../images/nav-4.d68723895f.png"><span>代付款</span></li>
				<li><img src="../images/nav-4.d68723895f.png"><span>待收货</span></li>
				<li><img src="../images/nav-4.d68723895f.png"><span>退换修</span></li>
			</ul>
		</div>
		<div class="kong-bai"></div>
		<div class="lei-biao">
			<div class="biao-ab" @click="tiao" ref="biao"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 会员中心</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>
			<div class="biao-ab" @click="tiao"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 我的优惠</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>
			<div class="kong-bai"></div>
		</div>

		<!-- <div class="kong-bai"></div> -->
		<div class="lei-biao">
			<div class="biao-ab" @click="tiao"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 会员中心</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>
			<div class="biao-ab" @click="tiao"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 会员中心</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>
			<div class="kong-bai"></div>
		</div>
		<!-- 	<div class="kong-bai"></div> -->
		<div class="lei-biao">
			<div class="biao-ab"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 会员中心</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>
			<div class="biao-ab" @click="tiao"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 会员中心</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>
			<div class="kong-bai"></div>
		</div>


		<div class="lei-biao">
			<div class="biao-ab" @click="tiao"><img src="../images/i-setting.fb9625b3f2.png">
				<span> 会员中心</span>
				<span class="biao-tu"><img src="../images/QQ截图20190924165926.png" /></span>
			</div>


		</div>
		
		
	</div>


		
</template>

<script>
	export default {
		name: "User",
		data() {
			return {
				isLogin: existCookie('token')
				
				
			}

		},
		mounted() {
			this.$eventBus.$emit('showHideNav', true);
		},
		methods: {
			toLogin() {	
				this.$router.push({
					name: 'login'
				})
			},
			tiao() {
				if (existCookie('token')) {
					//此处用于跳转其他页面
				} else {
					this.$router.push({
						name: 'login'
					})
				}

			},
			dingdan() {
				if (existCookie('token')) {
					//此处用于跳转其他页面
				} else {
					this.$router.push({
						name: 'login'
					})
				}

			}
		},

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
	.toubu {
		width: 100%;
		height: 160px;
		background: #ff6700;
	}

	.lg {
		width: 100%;
		/* line-height: 160px; */
		background: #ff6700;
	}

	.lg>img {
		width: 96px;
		height: 96px;
		padding-left: 40px;
		padding-top: 30px;
		float: left;
	}

	.dlu {
		background: #ff6700;
		float: left;
		/* font-size: .28rem; */
	}

	.dlu>p {
		font-size: .28rem;
		padding-top: .6rem;
		padding-left: .3rem;
		color: white;
	}

	.lg-hu {
		float: left;
		font-size: .36rem;
		padding-left: 40px;
		padding-top: 70px;
	}

	.dingdan {
		height: 80px;
		line-height: 80px;
		border-bottom: solid 1px #ff6700;
	}

	.wode {
		padding-left: 40px;
		float: left;
		font-size: .28rem;
	}

	.quanbu {
		font-size: .28rem;
		float: right;
		padding-right: 40px;
	}

	.serve {
		height: 170px;
		text-align: center;
	}

	.serve-ul {}

	.serve>ul>li {
		width: .72rem;
		height: .9rem;
		padding: 0 .85rem;
		float: left;
		padding-top: .3rem;

	}

	..serve>ul>li>img {
		padding-top: 50px;
	}

	.kong-bai {
		height: .2rem;
		background: #f5f5f5;
	}

	.biao-ab {
		height: 1.04rem;
		border-bottom: solid 1px #ff6700;
	}

	.biao-ab>img {
		padding-left: 40px;
		padding-top: 10px;
		float: left;

	}

	.biao-ab>span {
		font-size: .28rem;
		font-style: normal;
		color: rgba(0, 0, 0, .87);
		float: left;
		padding-top: .25rem;
		padding-left: .3rem;
	}

	.biao-tu {
		float: right;
	}

	.biao-tu>img {
		width: .3rem;
		float: left;
		height: .33rem;
		padding-left: 4rem;
	}
</style>
