<template>
  <div>
    <el-container style="height: 700px; border: 1px solid #eee">
      <el-header>tilas Intelligent learning aid system </el-header>

      <el-container>
        <el-aside
          width="200px"
          style="background-color: rgb(238, 241, 246) height: 700px; border: 1px solid #eee"
        >
          <el-menu :default-openeds="['1', '3']">
            <el-submenu index="1">
              <template slot="title"
                ><i class="el-icon-message"></i>information manager</template
              >
              <el-menu-item-group>
                <el-menu-item index="1-1">
                  <router-link to="/ele">apartment manager</router-link>  
                </el-menu-item>
                <el-menu-item index="1-2">
                  <router-link to="/emp">staff manager</router-link>  
                </el-menu-item>
              </el-menu-item-group>
            </el-submenu>
          </el-menu>
        </el-aside>

        <el-main>
          <el-form :inline="true" :model="searchForm" class="demo-form-inline">
            <el-form-item label="姓名">
              <el-input v-model="searchForm.name" placeholder="姓名"></el-input>
            </el-form-item>
            <el-form-item label="性别">
              <el-select v-model="searchForm.gender" placeholder="性别">
                <el-option label="男" value="1"></el-option>
                <el-option label="女" value="2"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="入职日期">
              <el-date-picker
                v-model="searchForm.entrydate"
                type="daterange"
                range-separator="至"
                start-placeholder="开始日期"
                end-placeholder="结束日期"
              >
              </el-date-picker>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">查询</el-button>
            </el-form-item>
          </el-form>

          <el-table :data="tableData" border>
            <el-table-column prop="name" label="姓名" width="130">
            </el-table-column>
            <el-table-column label="图片" width="130">
              <template slot-scope="scope">
                <img :src="scope.row.image" width="100px" height="70px">
              </template>
            </el-table-column>
            <el-table-column prop="gender" label="性别" width="130">
              <template slot-scope="scope">
                {{ scope.row.gender == 0 ? "女" : "男" }}
              </template>
            </el-table-column>
            <el-table-column prop="job" label="职位" width="130">
            </el-table-column>
            <el-table-column prop="entrydate" label="入职日期" width="130">
            </el-table-column>
            <el-table-column prop="updatetime" label="最后操作时间" width="130">
            </el-table-column>
            <el-table-column label="操作">
              <el-button type="primary" size="mini">编辑</el-button>
              <el-button type="danger" size="mini">删除</el-button>
            </el-table-column>
          </el-table>
          <br />
          <br />
          <el-pagination
            background
            layout="total,sizes, prev, pager, next, jumper"
            :total="1000"
            @size-change="handleSizeChange"
            @current-change="handleCurrentChange"
          >
          </el-pagination>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      tableData: [],
      searchForm: {
        name: "",
        gender: "",
        entrydate: [],
      },
    };
  },
  methods: {
    onSubmit: function () {
      alert("查询");
    },
    handleSizeChange: function (val) {
      alert("每页记录数变化" + val);
    },
    handleCurrentChange: function (val) {
      alert("页码发生变化" + val);
    },
  },
  mounted() {
    axios
      .get(
        "https://mockapi.eolink.com/8W7hUe4137d22441c38a08b15cd0d234f3a1c51a203a342/user/list"
      )
      .then((result) => {
        this.tableData = result.data.data;
      });
  },
};
</script>

<style>
.el-header {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
  font-size: 40px;
}
.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
}
.el-main {
  background-color: #e9eef3;
  color: #333;
}
</style>

