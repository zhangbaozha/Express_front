<template>
  <view class="container">
    <form @submit.prevent="placeOrder">
      <view class="form-group">
        <text>收件人姓名</text>
        <input type="text" v-model="recipientname" />
      </view>
      <view class="form-group">
        <text>收件人电话</text>
        <input type="tel" v-model="recipientphone" />
      </view>
      <view class="form-group">
        <text>收件人地址</text>
        <textarea v-model="recipientaddress"></textarea>
      </view>
	  <view class="form-group">
	    <text>网点名称</text>
	    <textarea v-model="node"></textarea>
	  </view>
      <view class="button-container">
        <button class="submit-button" type="submit" @click="submitData">提交订单</button>
      </view>
    </form>
  </view>
</template>

<script>
export default {
  name: "PlaceOrder",
  data() {
    return {
      recipientname: "",
      recipientphone: "",
      recipientaddress: "",
	  node:''
    };
  },
  methods: {
   async submitData() {
   		
      const query = {
      	username: getApp().globalData.userName,
      	phone: getApp().globalData.phone,
		address: getApp().globalData.address,
   		recipientname: this.recipientname,
   		recipientphone: this.recipientphone,
   		recipientaddress:this.recipientaddress,
   		node:this.node
      }
   	
      console.log(query)
      const {data: res} = await uni.$http.post("package/addpackage",query)
		if(res === "Login_success"){
	  	uni.showToast({
	  	    title:"寄件成功",
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