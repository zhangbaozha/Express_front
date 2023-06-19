<template>
  <view class="container">
    <!-- 登录表单 -->
    <form class="login-form" @submit.prevent="login">
      <label class="form-item">
        用户名：
        <input type="text" @input="onUsername" :value="username" placeholder="请输入用户名" />
      </label>
      <label class="form-item">
        密码：
        <input type="password" v-model="password" placeholder="请输入密码" />
      </label>
      <button class="submit-btn" type="submit" @click="login">普通用户登录</button>
	  <button class="submit-btn" type="submit" @click="postmanlogin">快递员登录</button>
	  <button class="submit-btn" type="submit" @click="nodemanagerlogin">网点管理员登录</button>
    </form>


		
		
    <!-- 注册入口 -->
    <view class="register-link" @click="toRegister">
      还没有账号？去注册
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
	  onUsername(event) {
	  	console.log(event)
	  	this.username = event.target.value
	  },
	  
    // 登录操作
    async login() {
      // TODO：调用登录接口进行验证，并进行相应提示
	  const query = {
	  	username: this.username,
	  	password: this.password,	
	  }
	  
	  const {data: res} = await uni.$http.post("user/userlogin",query)
	  
	  if(res.username != undefined){
	  	uni.showToast({
	  	    title:"登录成功",
	  	    duration:1000
	  	});
		getApp().globalData.userName = this.username
		getApp().globalData.password = this.password
		getApp().globalData.phone = res.phone
		getApp().globalData.address = res.address
		getApp().globalData.birth = res.birth
		
		uni.switchTab({
			url: "/pages/my/my?username="+this.username+"&password="+this.password
		 })
	  }
		else{
			uni.showToast({
			    title:"登录失败",
				icon:'none',
			    duration:1000
			});
		}
	  	  	
	  },
	  
	  
	  
	  async postmanlogin() {
	    // TODO：调用登录接口进行验证，并进行相应提示
	    const query = {
	    	username: this.username,
	    	password: this.password,	
	    }
	    
	    const {data: res} = await uni.$http.post("postman/postmanlogin",query)
	    
	    if(res.username != undefined){
	    	uni.showToast({
	    	    title:"登录成功",
	    	    duration:1000
	    	});
		getApp().globalData.node = res.node
	  	
	  	uni.navigateTo({
	  		url: "/pages/Postman/Postman"
	  	 })
	    }
	  	else{
	  		uni.showToast({
	  		    title:"登录失败",
	  			icon:'none',
	  		    duration:1000
	  		});
	  	}
	    	  	
	    },
		
		
		async nodemanagerlogin() {
		  // TODO：调用登录接口进行验证，并进行相应提示
		  const query = {
		  	username: this.username,
		  	password: this.password,	
		  }
		  
		  const {data: res} = await uni.$http.post("nodemanager/nodemanagerlogin",query)
		  
		  if(res.username != undefined){
		  	uni.showToast({
		  	    title:"登录成功",
		  	    duration:1000
		  	});
				getApp().globalData.node = res.node
			
			uni.navigateTo({
				url: "/pages/NodeManager/NodeManager"
			 })
		  }
			else{
				uni.showToast({
				    title:"登录失败",
					icon:'none',
				    duration:1000
				});
			}
		  	  	
		  }
	  
    },
}
	
	
    // 跳转到注册页面

</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.login-form {
  display: flex;
  flex-direction: column;
  margin-top: 100px;
}

.form-item {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  font-size: 16px;
  color: #333;
}

input {
  width: 200px;
  height: 32px;
  margin-left: 10px;
  border-radius: 5px;
  outline: none;
  border: 1px solid #dedede;
  padding: 4px 8px;
}

input::placeholder {
  color: #ccc;
}

.submit-btn {
  width: 150px;
  height: 36px;
  margin-top: 20px;
  background-color: #409EFF;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  outline: none;
  font-size: 16px;
  transition: background-color .3s ease, color .3s ease;
}

.submit-btn:hover {
  background-color: #66B1FF;
}

.register-link {
  display: block;
  margin-top: 40px;
  font-size: 16px;
  color: #409EFF;
  cursor: pointer;
}
</style>