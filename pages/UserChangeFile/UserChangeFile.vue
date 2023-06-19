<template>
  <view class="container">
    <form @submit.prevent="submitData">
        <!-- 手机号 -->
        <view class="form-group">
          <label for="phone">手机号：</label>
          <input type="tel" id="phone" name="phone" v-model="phone" required />
        </view>

        <!-- 出生日期 -->
        <view class="form-group">
          <label for="birthDate">出生日期：</label>
          <input type="date" id="birthDate" name="birthDate" v-model="birthDate" required />
        </view>

        <!-- 地址 -->
        <view class="form-group">
          <label for="address">地址：</label>
          <textarea id="address" name="address" v-model="address" required></textarea>
        </view>

        <!-- 提交按钮 -->
        <button type="submit" @click="submitData">提交</button>
    </form>
  </view>
</template>

<script>
export default {
  data() {
    return {
      phone: '', // 手机号
      birthDate: '', // 出生日期
      address: '', // 地址
    };
  },

  methods: {
    async submitData() {
		
     const query = {
     	username: getApp().globalData.userName,
     	password: getApp().globalData.password,
		phone: this.phone,
		birthDate: this.birthDate,
		address:this.address
		
     }
	 getApp().globalData.phone = this.phone
	 getApp().globalData.birth = this.birthDate
	 getApp().globalData.address = this.address
     console.log(query)
     const {data: res} = await uni.$http.post("user/userchangefile",query)
    },
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-group {
  margin-bottom: 1rem;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

input[type='tel'],
textarea {
  width: 100%;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
}

button[type='submit'] {
  margin-top: 1rem;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  border: none;
  border-radius: 0.25rem;
  background-color: #007bff;
  color: #fff;
}
</style>