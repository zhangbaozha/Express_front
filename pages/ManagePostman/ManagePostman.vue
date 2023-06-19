<template>
  <view class="container">
   
    <button @click="toCheckPostman" class="btn">查看快递员</button>
    
    <button @click="toAddPostman" class="btn">新增快递员</button>
    
    <button @click="toFirePostman" class="btn">开除快递员</button>
	

  </view>
</template>

<script>
export default {
  methods: {
    // 跳转到查询网点快件页面
    toCheckPostman() {
      uni.navigateTo({
        url: '/pages/CheckPostman/CheckPostman'
      })
    },
    // 跳转到录入快件信息页面
    toAddPostman() {
      uni.navigateTo({
        url: '/pages/AddPostman/AddPostman'
      })
    },
    // 跳转到修改快件状态页面
    toFirePostman() {
      uni.navigateTo({
        url: '/pages/FirePostman/FirePostman'
      })
    },
	toMangePostman() {
	  uni.navigateTo({
	    url: '/pages/PostmanChangeStatus/PostmanChangeStatus'
	  })
	},
	toCheckComplaint() {
	  uni.navigateTo({
	    url: '/pages/PostmanChangeStatus/PostmanChangeStatus'
	  })
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

.btn {
  margin: 20px;
  padding: 15px 30px;
  font-size: 16px;
  color: white;
  background-color: #2d8cf0;
  border: none;
  border-radius: 5px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
}
</style>