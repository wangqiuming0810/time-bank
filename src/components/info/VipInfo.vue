<template>
  <div>
    <HeaderTop></HeaderTop>
    <Navbar></Navbar>
<!--    <h2 style="width: 1100px;margin: 0px auto;background-color: #fff2e9;text-align: center">基本信息</h2>-->
    <div class="info">
      <el-descriptions class="margin-top" title="个人信息" :column="3" :size="size" border>
        <template slot="extra">
          <el-button type="primary" size="small" @click="dialogFormVisible1 = true">修改个人信息</el-button>
        </template>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-user"></i>
            用户名
          </template>
          {{info.username}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-mobile-phone"></i>
            用户ID
          </template>
          {{info.userid}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-location-outline"></i>
            身份证号
          </template>
          {{info.idcard}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-tickets"></i>
            性别
          </template>
          {{info.sex}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-office-building"></i>
            生日
          </template>
          {{info.birthday}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-office-building"></i>
            地址
          </template>
          {{info.address}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-office-building"></i>
            邮政编码
          </template>
          {{info.postcode}}
        </el-descriptions-item>
        <el-descriptions-item>
          <template slot="label">
            <i class="el-icon-office-building"></i>
            能力
          </template>
          {{info.ability}}
        </el-descriptions-item>
      </el-descriptions>
    </div>
    <el-dialog title="结束服务" :visible.sync="dialogFormVisible1" class="datafrom">
      <el-form :model="UpdateInfo">
        <el-form-item label="能力">
          <el-input v-model="UpdateInfo.userid"></el-input>
        </el-form-item>
        <el-form-item label="用户姓名">
          <el-input v-model="UpdateInfo.username"></el-input>
        </el-form-item>
        <el-form-item label="身份证号">
          <el-input v-model="UpdateInfo.idcard"></el-input>
        </el-form-item>
        <el-form-item label="性别">
          <el-input v-model="UpdateInfo.sex"></el-input>
        </el-form-item>
        <el-form-item label="出生日期">
          <el-input v-model="UpdateInfo.birthday"></el-input>
        </el-form-item>
        <el-form-item label="地址">
          <el-input v-model="UpdateInfo.address"></el-input>
        </el-form-item>
        <el-form-item label="邮政编码">
          <el-input v-model="UpdateInfo.postcode"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="cancel">取 消</el-button>
        <el-button type="primary" @click="submit">确 定</el-button>
      </div>
    </el-dialog>


  </div>
</template>

<script>
import HeaderTop from '@/components/home/HeaderTop.vue'
// import NavBar from '@/components/home/Nav-Bar';
import Navbar from '@/components/home/Nav-Bar'
export default {
  components: {
    HeaderTop,
    // NavBar
    Navbar
  },
  name: "VipInfo",
  data(){
    return{
      info:{
        username:'12345678',
        userid:'23546',
        idcard:'44685',
        sex: '22222',
        birthday: '1234',
        address: '46667',
        postcode: '4443',
        ability: '23555'
      },
      UpdateInfo: {
        userid:'23546',
        username:'12345678',
        idcard:'44685',
        sex: '22222',
        birthday: '1234',
        address: '46667',
        postcode: '4443',
        ability: '23555'
      },
      dialogFormVisible1:false
    }
  },
  mounted:{
    getinfo(){

    }
  },
  methods:{
    submit() {
      this.dialogFormVisible1 = false
      this.$http.post('api/v1/DoneServicing',this.UpdateInfo).then(res => {
        console.log(res)
        this.$message.success('添加成功')
      }).catch(err => {
        console.log(err,"添加失败，请求出错")
      })
    },
    cancel() {
      this.dialogFormVisible1 = false
    },
  }
}
</script>

<style scoped>

.info{
  width: 1100px;
  margin: 0 auto;

}

</style>
