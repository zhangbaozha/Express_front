<template>
  <view class="container">
    <!-- 寄件按钮 -->
    <button type="button" class="btn btn-post" @click="goToPost">寄件</button>

    <!-- 取件按钮 -->
    <button type="button" class="btn btn-receive" @click="goToReceive">取件</button>
  </view>
</template>

<script>
export default {
  methods: {
    goToPost() {
      uni.navigateTo({
        url: '/pages/post/post',
      });
    },

    goToReceive() {
      uni.navigateTo({
        url: '/pages/receive/receive',
      });
    },
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}

.btn {
  width: 80%;
  margin-top: 1rem;
  padding: 1rem;
  font-size: 1.5rem;
  line-height: 1.5;
  border: none;
  border-radius: 0.25rem;
  color: #fff;
  cursor: pointer;
}

.btn-post {
  background-color: #007bff;
}

.btn-receive {
  background-color: #dc3545;
}
</style>