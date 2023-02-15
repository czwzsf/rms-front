<template>
  <div>
    <el-container style="height: 100%; border: 1px solid #eee">
      <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
        <el-menu>
          <el-submenu index="1">
            <template slot="title">车型驾驶舱</template>
            <el-menu-item-group title="解放">
              <!--              <template slot="title">解放</template>-->
              <el-menu-item index="1-1">J6工程</el-menu-item>
              <el-menu-item index="1-2">J7公路</el-menu-item>
              <el-menu-item index="1-2">J6公路</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="青汽">
              <el-menu-item index="1-4">JH6</el-menu-item>
              <el-menu-item index="1-5">悍v</el-menu-item>
              <el-menu-item index="1-6">J6f</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="成都">
              <el-menu-item index="1-4">J6公路</el-menu-item>
            </el-menu-item-group>
            <!--            <el-submenu index="1-4">-->
            <!--              <template slot="title">选项4</template>-->
            <!--              <el-menu-item index="1-4-1">选项4-1</el-menu-item>-->
            <!--            </el-submenu>-->
          </el-submenu>
          <el-submenu index="2">
            <template slot="title">平台驾驶舱</template>
            <el-menu-item-group>
              <template slot="title">锡柴发动机</template>
              <el-menu-item index="2-1-1">6DM</el-menu-item>
              <el-menu-item index="2-1-2">6DL</el-menu-item>
              <el-menu-item index="2-1-3">6DlD</el-menu-item>
              <el-menu-item index="2-1-4">4DLD</el-menu-item>
              <el-menu-item index="2-1-5">6SM</el-menu-item>
              <el-menu-item index="2-1-6">4DB</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="大柴发动机">
              <el-menu-item index="2-2-1">4DK</el-menu-item>
              <el-menu-item index="2-2-2">6DK</el-menu-item>
              <el-menu-item index="2-2-3">4DH</el-menu-item>
              <el-menu-item index="2-2-4">6DH</el-menu-item>
              <el-menu-item index="2-2-5">4Dd</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="变速箱">
              <el-submenu index="2-3">
                <template slot="title">国产变速箱</template>
                <el-menu-item index="2-3-1">国产变速箱1</el-menu-item>
                <el-menu-item index="2-3-2">国产变速箱2</el-menu-item>
              </el-submenu>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title">零部件驾驶舱</template>
            <el-menu-item-group>
              <template slot="title">锡柴发动机</template>
              <el-menu-item index="3-1-1">索赔TOP30零部件</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="大柴发动机">
              <el-menu-item index="3-2-1">索赔TOP30零部件</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="变速箱车桥">
              <el-menu-item index="3-3-1">索赔TOP30零部件</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title">基础数据维护</template>
            <el-menu-item-group>
              <el-menu-item index="4-1-1">对照表</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group>
              <el-menu-item index="4-2-1">销售索赔数据</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group>
              <el-menu-item index="4-3-1">下载</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-container>
        <el-header style="text-align: right; font-size: 12px">
          <el-dropdown>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>查看</el-dropdown-item>
              <el-dropdown-item>新增</el-dropdown-item>
              <el-dropdown-item>删除</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <span>陈喆伟</span>
        </el-header>

        <el-main>
          <el-table :data="tableData">
            <el-table-column prop="date" label="日期" width="140">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
            <el-table-column prop="address" label="地址">
            </el-table-column>
          </el-table>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "rmsMenu",
  data() {
    const item = {
      date: '2016-05-02',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1518 弄'
    };
    return {
      tableData: Array(15).fill(item)
    }
  },
}
</script>

<style scoped>
.el-header {
  background-color: #B3C0D1;
  color: #333;
  line-height: 60px;
}

.el-aside {
  color: #333;
}
</style>
