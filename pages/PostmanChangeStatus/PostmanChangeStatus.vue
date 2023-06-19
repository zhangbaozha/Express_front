<template>
  <view class="container">
    <form @submit.prevent="placeOrder">
		
		
		<view class="form-group">
		  <text>订单号</text>
		  <input type="text" v-model="code" />
		</view>
		<view class="form-group">
		  <text>修改状态</text>
		  <input type="tel" v-model="status" />
		</view>
		
	  
      <view class="button-container">
        <button class="submit-button" type="submit" @click="submitData">确认修改</button>
      </view>
    </form>
  </view>
</template>

<script>
export default {
  name: "PlaceOrder",
  data() {
    return {
		code:'',
		status:''
    };
  },
  methods: {
   async submitData() {
   		
      const query = {
      	code: this.code,
      	status: this.status,
		
		
      }
   	
     
      const {data: res} = await uni.$http.post("postman/postmanchangestatus",query)
		if(res === "success"){
	  	uni.showToast({
	  	    title:"修改成功",
	  	    duration:1000
	  	});
		}
		else{
			uni.showToast({
			    title:"查询不到此快递",
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