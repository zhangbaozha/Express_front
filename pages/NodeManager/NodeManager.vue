<template>
  <view class="container">
    <!-- 查询网点快件 -->
    <button @click="toCheckNodePackage" class="btn">查询网点快件</button>
    <!-- 录入快件信息 -->
    <button @click="toAddPackage" class="btn">录入快件信息</button>
    <!-- 修改快件状态 -->
    <button @click="toChangeStatus" class="btn">修改快件状态</button>
	
	<button @click="toMangePostman" class="btn">管理网点员工</button>
	
	<button @click="toCheckComplaint" class="btn">查看投诉信息</button>
	
  </view>
</template>

<script>
export default {
  methods: {
    // 跳转到查询网点快件页面
    toCheckNodePackage() {
      uni.navigateTo({
        url: '/pages/CheckNodePackage/CheckNodePackage'
      })
    },
    // 跳转到录入快件信息页面
    toAddPackage() {
      uni.navigateTo({
        url: '/pages/PostmanAddPackage/PostmanAddPackage'
      })
    },
    // 跳转到修改快件状态页面
    toChangeStatus() {
      uni.navigateTo({
        url: '/pages/PostmanChangeStatus/PostmanChangeStatus'
      })
    },
	toMangePostman() {
	  uni.navigateTo({
	    url: '/pages/ManagePostman/ManagePostman'
	  })
	},
	toCheckComplaint() {
	  uni.navigateTo({
	    url: '/pages/CheckComplaint/CheckComplaint'
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