<template>
	<view class="login-container">
		<uni-icons type="contact-filled" size=100 color="#AFAFAF"></uni-icons>
		<button type="primary" class="btn-login" @click="gotoMyReceive">查看我的待收快件</button>
		<button type="primary" class="btn-login" @click="gotoMySend">查看我寄出的快件</button>
		<button type="primary" class="btn-login" @click="gotoUserChangeFile">修改个人资料</button>
		<button type="primary" class="btn-login" @click="gotoComplain">投诉与反馈</button>
		
	</view>
</template>

<script>
	export default {
		onLoad(options) {
			this.username = options.username
			this.password = options.password
			console.log(getApp().globalData.userName)
		
		},
		data() {
			return {
				username: '',
				password: ''
			};
		},
		methods:{
			gotoMyReceive(){
				uni.navigateTo({
					url: "/pages/MyReceive/MyReceive"
				})
			},
			gotoMySend(){
				uni.navigateTo({
					url: "/pages/MySend/MySend"
				})
			},
			gotoUserChangeFile(){
				uni.navigateTo({
					url: "/pages/UserChangeFile/UserChangeFile"
				})
			},
			gotoComplain(){
				uni.navigateTo({
					url: "/pages/Complain/Complain"
				})
			}
		}
	}
</script>

<style lang="scss">
.login-container{
		height: 750rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		.btn-login{
			width: 90%;
			border-radius: 100px;
			margin: 15px 0;
			background-color: red;
		}
		
	}
</style>
