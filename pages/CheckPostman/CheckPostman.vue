<template>
	<view>
		
		  <view class="package-list">
		    <!-- 遍历包裹列表数据 -->
		    <view v-for="(pkg, index) in postmanList" :key="index">
		      <li>
		        
		          <div slot="content" class="uni-card__content">
		            <p>快递员姓名：{{ pkg.username }}</p>
		           
		          </div>
		          <div slot="footer" class="uni-card__footer">{{ pkg.status }}</div>
		        
		      </li>
		    </view>
		  </view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				postmanList: [],
				
			};
		},
		onLoad(){
			this.getPostmanList()
		},
		methods:{
			async getPostmanList(){
				getApp().globalData.nodemanagernode
				console.log(postmen)
				const {data: postmen} = await uni.$http.get("nodemanager/nodemanagercheckpostman?node="+getApp().globalData.node)
				console.log(postmen)
				this.postmanList = postmen
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