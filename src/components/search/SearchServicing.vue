<template>
  <div>
    <HeaderTop></HeaderTop>
    <Navbar></Navbar>
    <div class="search-input">
      <h2 style="margin: 20px 0px">搜索未结束的服务</h2>
      <el-input
          placeholder="请输入被服务人id"
          v-model="form.elderID"
          style="width: 200px;"
      >
      </el-input>
      <el-input
          placeholder="请输入服务类型"
          v-model="form.jobID"
          style="width: 200px;"
      >
      </el-input>
      <el-button type="primary" icon="el-icon-search" @click="serch">搜索</el-button>
      <div style="margin: 20px 0px">
        <h2>服务信息</h2>
        <el-table
            :data="ServeData"
            stripe
            style="width: 100%">
          <el-table-column
              prop="ServicingCount"
              label="ServicingCount"
              width="180">
          </el-table-column>
          <el-table-column
              prop="ServicingOlderID"
              label="ServicingOlderID"
              width="180">
          </el-table-column>
          <el-table-column
              prop="ServicingState"
              label="ServicingState">
          </el-table-column>

          <el-table-column
              prop="ServicingType"
              label="ServicingType">
          </el-table-column>

          <el-table-column
              prop="ServicingValue"
              label="ServicingValue">
          </el-table-column>

          <el-table-column
              prop="ServicingVolID"
              label="ServicingVolID">
          </el-table-column>

          <el-table-column
              prop="StartTime"
              label="StartTime">
          </el-table-column>

        </el-table>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderTop from '@/components/home/HeaderTop.vue'
import Navbar from '@/components/home/Nav-Bar'
export default {
  components: {
    HeaderTop,
    Navbar
  },
  name: "SearchServicing",
  data(){
    return{
      form: {
        elderID: '',
        jobID: ''
      },
      ServeData:[
        {
          ServicingCount: '1',
          ServicingOlderID: '2',
          ServicingState: '3',
          ServicingType: '4',
          ServicingValue: '5',
          ServicingVolID: '6',
          StartTime: '7'
        }
      ]
    }
  },
  methods:{
    serch(){
      if(this.form.elderID == '' || this.form.jobID == '') {
        this.$message({
          message: '请输入被服务人id和服务类型',
          type: 'warning'
        })
        return
      }
      this.$http.post('api/v1/ServicingStatusList',this.form).then(res => {
        console.log(res)
        this.ServeData = res.data.data
        this.$message.success('查询成功')
      }).catch(err => {
        console.log(err)
        this.$message.error('查询出错')
      })
    }
  }
}
</script>

<style scoped>

.search-input{
  width: 1100px;
  margin: 0 auto;
}

</style>
