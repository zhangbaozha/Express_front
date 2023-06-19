<template>
  <view class="container">
    <form @submit.prevent="placeOrder">
		
		
		<view class="form-group">
		  <text>快递员姓名</text>
		  <input type="text" v-model="username" />
		</view>
		<view class="form-group">
		  <text>密码</text>
		  <input type="tel" v-model="password" />
		</view>
		
	  
      <view class="button-container">
        <button class="submit-button" type="submit" @click="submitData">确认添加</button>
      </view>
    </form>
  </view>
</template>

<script>
export default {
  name: "PlaceOrder",
  data() {
    return {
		username:'',
		password:''
    };
  },
  methods: {
   async submitData() {
   		
      const query = {
      	username: this.username,
      	password: this.password,
		node : getApp().globalData.node
		
      }
   	
     
      const {data: res} = await uni.$http.post("nodemanager/addpostman",query)
		if(res === "success"){
	  	uni.showToast({
	  	    title:"新增成功",
	  	    duration:1000
	  	});
		}
		else{
			uni.showToast({
			    title:"新增失败",
				icon:'none',
			    duration:1000
			});
		}
  }
  }
};
</script>

<style scoped>
.container {
  padding: 20px;
}

.form-group {
  margin-bottom: 10px;
}

input,
textarea {
  border-radius: 4px;
  border: 1px solid #ccc;
  padding: 5px;
  width: 100%;
  box-sizing: border-box;
}

.submit-button {
  background-color: #007aff;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 10px;
  width: 100%;
  font-size: 16px;
}

.button-container {
  margin-top: 20px;
}
</style>