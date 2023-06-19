<template>
  <view class="container">
    <!-- 投诉信息文本框 -->
    <textarea v-model="content" placeholder="请输入投诉信息" class="textarea"></textarea>
    <!-- 提交按钮 -->
    <button @click="submitComplaint" class="btn">提交</button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      content: '' // 用户输入的投诉信息
    }
  },
   methods: {
    async submitComplaint() {
      if (this.content.trim() === '') {
        uni.showToast({
          title: '请填写投诉信息',
          icon: 'none'
        })
        return
      }
      
      // 发送投诉信息给后端
      // 这里可以调用后端接口或进行其他操作
	  const query = {
	  	content: this.content
	  		
	  }
	  
	  const {data: res} = await uni.$http.post("complaint/addcomplaint",query)
	  
	  if(res === "success"){
	  uni.showToast({
	      title:"反馈成功",
	      duration:1000
	  });
	  }
	  else{
	  	uni.showToast({
	  	    title:"反馈失败",
	  		icon:'none',
	  	    duration:1000
	  	});
	  }
      
      uni.showToast({
        title: '投诉信息已提交',
        duration: 2000
      })
      
      // 提交成功后重置投诉信息
      this.complaint = ''
    }
  }
}
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f5f5f5;
}

.textarea {
  width: 80%;
  height: 200px;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ddd;
  resize: none;
}

.btn {
  margin-top: 20px;
  padding: 15px 30px;
  font-size: 16px;
  color: white;
  background-color: #2d8cf0;
  border: none;
  border-radius: 5px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
}
</style>