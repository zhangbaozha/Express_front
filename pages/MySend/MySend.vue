<template>
	<view>
		
		  <view class="package-list">
		    <!-- 遍历包裹列表数据 -->
		    <view v-for="(pkg, index) in packageList" :key="index">
		      <li>
		        <!-- 包裹卡片组件 -->
		        <uni-card :title="pkg.code" :has-footer="true">
		          <div slot="content" class="uni-card__content">
		            <p>寄件人姓名：{{ pkg.sendername }}</p>
		            <p>寄件人电话：{{ pkg.senderphone }}</p>
		            <p>寄件人地址：{{ pkg.senderaddress }}</p>
		            <p>收件人姓名：{{ pkg.recipientname }}</p>
		            <p>收件人电话：{{ pkg.recipientphone }}</p>
		            <p>收件人地址：{{ pkg.recipientaddress }}</p>
		            <p>快件状态：{{ pkg.status }}</p>
		          </div>
		          <div slot="footer" class="uni-card__footer">{{ pkg.status }}</div>
		        </uni-card>
		      </li>
		    </view>
		  </view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				packageList: [],
				
			};
		},
		onLoad(){
			this.getPackageList()
		},
		methods:{
			async getPackageList(){
				const {data: packages} = await uni.$http.get("package/mysend?phone="+getApp().globalData.phone)
				console.log(packages)
				this.packageList = packages
			},
			
		}
	}
</script>
<style>
  /* 包裹列表容器 .package-list */
  .package-list {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      padding: 10px;
      background-color: #f5f5f5;
  }

  /* 卡片容器 uni-card */
  uni-card {
      width: 45%;
      margin-bottom: 20px;
      background-color: white;
  }

  /* 卡片标题 .card-title */
  .card-title {
      text-align: center;
      font-size: 18px;
      color: #2d8cf0;
  }

  /* 内容容器 .uni-card__content */
  .uni-card__content {
      padding: 15px;
      font-size: 14px;
      line-height: 26px;
      color: #666;
  }

  /* 底部容器 .uni-card__footer */
  .uni-card__footer {
      padding: 10px;
      background-color: #f5f5f5;
      text-align: right;
      font-size: 12px;
      color: #999;
  }
</style>