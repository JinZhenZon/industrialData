<template>
    <!-- <div>{{count}}</div> -->
    <div style="background:#eee;">

          <tableHeader style="margin-top:20px;">
            <div slot="pagetitle">预立案栏</div>
        </tableHeader>
        
        <div style="width:98%;margin:0 auto;">
            
            <el-table
    target="#mylist"
    :data="tableData"
    stripe
    :show-header="true"
    border
    style="width: 100%;height:800px;margin-top:20px;">
    <el-table-column 
      prop="num"
      label="任务号" align="center" style = "height:100px;">
    </el-table-column>
    <el-table-column
       prop="projectFrom"
      label="问题来源" align="center">
    </el-table-column>
    <el-table-column
       prop="bigName"
      label="大类名称" align="center">
    </el-table-column>
    <el-table-column
       prop="smallName"
      label="小类名称" align="center">
    </el-table-column>
    <el-table-column
       prop="addresdesc"
      label="地址描述" align="center">
    </el-table-column>
        <el-table-column
       prop="projectdesc"
      label="问题描述" align="center">
    </el-table-column>
  </el-table>
    <el-row id="fenye">
    <el-col>
    <el-pagination
    background
    layout="prev, pager, next"
    :page-count="Math.ceil(homeData.length/15)" @current-change="handleCurrentChange">
    </el-pagination>
    </el-col>
    </el-row>

        </div>

    </div>
</template>

<script>
import {mapState} from 'vuex'
import tableHeader from "../table-header";
export default {
    computed: {
      ...mapState({
         homeData: state => state.town.casebar
    }),
      tableData(){
       return this.homeData.slice(this.start,this.end);
      }
    },
      data() {
      return {
        activeIndex: 'all',
        start : 0 ,
        end : 15,
      };
    },
    methods: {
       handleCurrentChange(val) {
        this.start=(`${val}`-1)*15;
        this.end=(`${val}`)*15;
      }
    },
     created () {        
    },
    components: {
        tableHeader,
    }
}
</script>

<style scoped>
.el-menu--horizontal .el-menu-item{
    font-size:20px;
    line-height: 72px;
    margin-left:80px;
}
.pagetitle{
    font-size:18px;
    line-height:50px;
}

  .list_title{
        font-size:18px;
        line-height:78px;
        font-weight: 800;
    }
    #table_title{
        font-size:16px;
        line-height:70px;
        text-align: center
    }
    #fenye{
        width:100%;
        background:#fff;
        text-align:center;
        line-height: 34px;
        padding-top:40px;
    }

</style>
