<template>
  <div>
    <el-container style="height: 100%; border: 1px solid #eee">
      <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
        <el-menu>
          <el-submenu index="1">
            <template slot="title">故障件原始信息提交</template>
            <el-menu-item-group>
              <!--              <template slot="title">解放</template>-->
              <el-menu-item index="1-1">常规返厂信息上传</el-menu-item>
              <el-menu-item index="1-2">单独返厂信息上传</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title">供应商故障件分析填报</template>
            <el-menu-item-group>
              <template slot="title"></template>
              <el-menu-item index="2-1-1">批量信息填报</el-menu-item>
              <el-menu-item index="2-1-2">逐项信息填报</el-menu-item>
              <el-menu-item index="2-1-3">填报信息修改审定</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title">故障件分析监控</template>
            <el-menu-item index="3-1-1">故障分析情况</el-menu-item>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title">基础数据维护</template>
            <el-menu-item-group>
              <el-menu-item index="4-1-1">故障模式维护</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group>
              <el-menu-item index="4-2-1">原始信息维护</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group>
              <el-menu-item index="4-3-1">故障分析信息维护</el-menu-item>
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
          <div>
            <h3 style="text-align: left">常规返厂信息上传</h3>
            <el-upload
                class="upload-demo"
                action="https://jsonplaceholder.typicode.com/posts/"
                :on-change="handleChange"
                :file-list="fileList"
                style="text-align: left"
                accept=".xlsx, .xls">
              <el-button size="small" type="primary">点击上传</el-button>
            </el-upload>
            <h3 style="text-align: left">单独返厂信息上传</h3>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm"
                     style="text-align: left" :inline="true">
              <el-form-item label="零部件名称" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
              </el-form-item>
              <el-form-item label="发动机号" prop="region">
                <el-input v-model="ruleForm.region"></el-input>
              </el-form-item>
              <el-form-item label="故障件前7位" prop="Fault_piece_code">
                <el-input v-model="ruleForm.Fault_piece_code"></el-input>
              </el-form-item>
              <el-form-item label="故障里程" prop="Breakdown_mileage">
                <el-input v-model="ruleForm.Breakdown_mileage"></el-input>
              </el-form-item>
              <el-form-item label="故障模式" prop="Breakdown_type">
                <el-select v-model="Breakdown_type" filterable placeholder="请选择">
                  <el-option
                      v-for="item in ruleForm.Breakdown_type"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value"></el-option>
                </el-select>
              </el-form-item>
              <el-form-item>
                <el-button type="primary" @click="submitForm('ruleForm')">立即创建</el-button>
                <el-button @click="resetForm('ruleForm')">重置</el-button>
              </el-form-item>
            </el-form>
          </div>
        </el-main>
      </el-container>
    </el-container>
    <el-backtop target=".page-component__scroll .el-scrollbar__wrap"></el-backtop>
  </div>
</template>
<script>
export default {
  name: "rmsMenu",
  data() {
    return {
      fileList: [],
      Breakdown_type: [],
      ruleForm: {
        name: '',
        region: '',
        Fault_piece_code: '',
        Breakdown_mileage: '',
        Breakdown_type: [
          {
            value: '选项1',
            label: '故障模式1'
          },
          {
            value: '选项2',
            label: '故障模式2'
          },
          {
            value: '选项3',
            label: '故障模式3'
          },
          {
            value: '选项4',
            label: '故障模式4'
          },
          {
            value: '选项5',
            label: '故障模式5'
          }
        ],
      },
      rules: {
        name: [
          {required: true, message: '请输入零部件名称', trigger: 'blur'},
          {min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur'}
        ],
        region: [
          {required: true, message: '请输入发动机号', trigger: 'blur'}
        ],
        Fault_piece_code: [
          {required: true, message: '请输入故障件前7位代码', trigger: 'blur'},
          {min: 7, max: 7, message: '长度为7位', trigger: 'blur'}
        ],
        Breakdown_mileage: [
          {required: true, message: '请输入发动机号', trigger: 'blur'}
        ],
        Breakdown_type: [
          {required: true, message: '请选择故障模式', trigger: 'blur'}
        ]
      }
    };
  },
  methods: {
    handleChange(file, fileList) {
      this.fileList = fileList.slice(-3);
    },
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('submit!');
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
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
