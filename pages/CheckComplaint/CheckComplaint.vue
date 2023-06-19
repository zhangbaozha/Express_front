<template>
	 <view class="container">
	    <view v-if="complaintList.length === 0" class="empty">暂无投诉信息</view>
	    <view v-else>
	      <view class="item" v-for="(complaint, index) in complaintList" :key="index">
	        <!-- 投诉内容 -->
	        <view class="content">{{ complaint.content }}</view>
	        <!-- 投诉日期 -->
	        <view class="date">{{ complaint.date }}</view>
	        <!-- 分割线 -->
	        <view class="divider" v-if="index !== complaintList.length - 1"></view>
	      </view>
	    </view>
	  </view>
</template>

<script>
	export default {
		data() {
			return {
				complaintList: [],
				
			};
		},
		onLoad(){
			this.getComplaintList()
		},
		methods:{
			async getComplaintList(){
				const {data: complaints} = await uni.$http.get("complaint/findall")
				console.log(complaints)
				this.complaintList = complaints
			},
			
		}
	}
</script>
<style>
.container {
  padding: 20px;
}

.empty {
  text-align: center;
  margin-top: 100px;
  color: #999;
}

.item {
  margin-bottom: 10px;
  background-color: #fff;
  border-radius: 5px;
  padding: 10px;
}

.content {
  font-size: 16px;
  color: #333;
  margin-bottom: 5px;
}

.date {
  font-size: 12px;
  color: #999;
}

.divider {
  margin-top: 10px;
  height: 1px;
  background-color: #eee;
}
</style>