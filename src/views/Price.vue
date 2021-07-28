<template>
  <div class="columns">
    <div class="column is-12">
      <h1 class="title">請填寫以下表單，協助我們了解您的需求</h1>
      <el-steps :active="active" finish-status="success">
        <el-step title="步驟 1" description="基本資料"></el-step>
        <el-step title="步驟 2" description="需求釐清"></el-step>
        <el-step title="步驟 3" description="報價"></el-step>
        <el-step title="步驟 4" description="訂單生成"></el-step>
        <el-step title="完成訂單" description=""></el-step>
      </el-steps>

      <el-card class="box-card column is-6 is-offset-3">

        <h2 class="subtitle"> 下單 </h2>

        <el-card>
          <h2 class="subtitle"> 公司基本資料 </h2>
          <el-card>
            <div class="text item">
              <span>名稱</span>
            </div>
            <el-input v-model="input" placeholder="請輸入名稱"></el-input>
            <div class="text item">
              <span>統編</span>
            </div>
            <el-input v-model="input" placeholder="請輸入統編"></el-input>
            <div class="text item">
              <span>負責窗口</span>
            </div>
            <el-input v-model="input" placeholder="請輸入負責窗口"></el-input>
            <div class="text item">
              <span>電話</span>
            </div>
            <el-input v-model="input" placeholder="請輸入電話"></el-input>
            <div class="text item">
              <span> Line id</span>
            </div>
            <el-input v-model="input" placeholder="請輸入 Line id"></el-input>
            <div class="text item">
              <span>Email</span>
            </div>
            <el-input v-model="input" placeholder="請輸入 email"></el-input>
            <div class="text item">
              <span>業務需求</span>
              <p class="control">
              <span class="select">
                <select>
                  <option>進口</option>
                  <option>出口</option>
                </select>
              </span>
              </p>
            </div>
          </el-card>
          <el-card>
            <h2 class="subtitle">商品資訊</h2>
            <el-card>
              <div class="text item">
                <span>商品名稱(中文)</span>
              </div>
              <el-input v-model="input" placeholder="請輸入 email"></el-input>
              <div class="text item">
                <span>商品名稱(英文)</span>
              </div>
              <el-input v-model="input" placeholder="請輸入 email"></el-input>
              <div class="text item">
                <span>HS CODE (10碼)</span>
              </div>
              <el-input v-model="input" placeholder="請輸入 email"></el-input>
              <div class="text item">
                <span>DG / Non DG (MSDS安全資料表上傳)</span>
              </div>
              <el-upload
                  class="upload-demo"
                  action="https://jsonplaceholder.typicode.com/posts/"
                  :on-preview="handlePreview"
                  :on-remove="handleRemove"
                  :before-remove="beforeRemove"
                  multiple
                  :limit="3"
                  :on-exceed="handleExceed"
                  :file-list="fileList"
              >
                <el-button size="small" type="primary">點擊上傳</el-button>
              </el-upload>
                <div class="control is-horizontal">
                  <div class="control-label">
                    <label class="label">備註</label>
                  </div>
                  <div class="control">
                    <textarea class="textarea" placeholder="告訴我們其他需要幫助你們的地方"></textarea>
                  </div>
                </div>
            </el-card>
          </el-card>


        </el-card>
        <el-button style="margin-top: 12px;" @click="next">下一步</el-button>
      </el-card>


    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'Price',
  data() {
    return {
      active: 0,
    };
  },

  methods: {
    next() {
      if (this.active++ > 2) this.active = 0;
    },
}
,
mounted()
{
  document.title = 'Home | Price'
}
,
// methods: {
//   async getLatestProducts() {
//     this.$store.commit('setIsLoading', true)
//
//     await axios
//         .get('/api/v1/latest-products/')
//         .then(response => {
//           this.latestProducts = response.data
//         })
//         .catch(error => {
//           console.log(error)
//         })
//
//     this.$store.commit('setIsLoading', false)
//   }
}
</script>

<style scoped>

</style>