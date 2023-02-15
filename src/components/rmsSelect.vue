<template>
  <div>
    <el-container>
      <el-header>
        <header class="el-header" style="height: 60px; text-align: right; font-size: 12px;">
          <div class="el-dropdown"><i class="el-icon-setting el-dropdown-selfdefine" aria-haspopup="list"
                                      aria-controls="dropdown-menu-7730" role="button" tabindex="0"
                                      style="margin-right: 15px;"></i>
            <ul class="el-dropdown-menu el-popper" id="dropdown-menu-7730" style="display: none;">
              <li tabindex="-1" class="el-dropdown-menu__item"><!---->查看</li>
              <li tabindex="-1" class="el-dropdown-menu__item"><!---->新增</li>
              <li tabindex="-1" class="el-dropdown-menu__item"><!---->删除</li>
            </ul>
          </div>
          <span>王小虎</span></header>
      </el-header>
      <el-container>
        <el-aside width="200px">
          <el-menu
              default-active="2"
              class="el-menu-vertical-demo"
              @open="handleOpen"
              @close="handleClose"
              background-color="#545c64"
              text-color="#fff"
              active-text-color="#ffd04b">
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>零部件查询</span>
              </template>
            </el-submenu>
          </el-menu>
          <el-menu
              default-active="2"
              class="el-menu-vertical-demo"
              @open="handleOpen"
              @close="handleClose"
              background-color="#545c64"
              text-color="#fff"
              active-text-color="#ffd04b">
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>多维度分析</span>
              </template>
            </el-submenu>
          </el-menu>
          <el-menu
              default-active="2"
              class="el-menu-vertical-demo"
              @open="handleOpen"
              @close="handleClose"
              background-color="#545c64"
              text-color="#fff"
              active-text-color="#ffd04b">
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>零部件查询</span>
              </template>
            </el-submenu>
          </el-menu>
        </el-aside>
        <el-main>
          <!--月份选择-->
          <el-row>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <div class="block">
                  <span class="demonstration">报表月</span>
                  <el-date-picker
                      v-model="options4.value1"
                      align="right"
                      type="date"
                      placeholder="选择日期"
                      :picker-options="pickerOptions">
                  </el-date-picker>
                </div>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <div class="block">
                  <span class="demonstration">销售日期</span>
                  <el-date-picker
                      v-model="options4.value2"
                      align="right"
                      type="date"
                      placeholder="选择日期"
                      :picker-options="pickerOptions">
                  </el-date-picker>
                </div>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <div class="block">
                  <span class="demonstration">索赔日期</span>
                  <el-date-picker
                      v-model="options4.value3"
                      align="right"
                      type="date"
                      placeholder="选择日期"
                      :picker-options="pickerOptions">
                  </el-date-picker>
                </div>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <div class="block">
                  <span class="demonstration">生产日期</span>
                  <el-date-picker
                      v-model="options4.value4"
                      align="right"
                      type="date"
                      placeholder="选择日期"
                      :picker-options="pickerOptions">
                  </el-date-picker>
                </div>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <span>生产基地</span>
                <el-select v-model="value" filterable placeholder="请选择">
                  <el-option
                      v-for="item in options"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <span>车型</span>
                <el-select v-model="value" filterable placeholder="请选择">
                  <el-option
                      v-for="item in options"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <span>总成分类</span>
                <el-select v-model="value" filterable placeholder="请选择">
                  <el-option
                      v-for="item in options"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <span>机型</span>
                <el-select v-model="value" filterable placeholder="请选择">
                  <el-option
                      v-for="item in options"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="5">
              <div class="grid-content bg-purple">
                <span>零部件名称</span>
                <el-select v-model="selectedValue1" filterable placeholder="请选择">
                  <el-option
                      v-for="item in options1"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple-light">
                <span>供应商名称</span>
                <el-select v-model="selectedValue2" filterable :disabled="!selectedValue1" placeholder="请选择">
                  <el-option
                      v-for="item in options2[selectedValue1]"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content bg-purple">
                <div class="grid-content bg-purple-light">
                  <span>子组号</span>
                  <el-select v-model="selectedValue3" filterable :disabled="!selectedValue1" placeholder="请选择">
                    <el-option
                        v-for="item in options3[selectedValue1]"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                    </el-option>
                  </el-select>
                </div>
              </div>
            </el-col>
          </el-row>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "rmsSelect",
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  },
  data() {
    return {
      selectedValue1: null,
      selectedValue2: null,
      selectedValue3: null,
      // 零部件名称
      options1: [
        {value: 1, label: 'Option 1'},
        {value: 2, label: 'Option 2'},
        {value: 3, label: 'Option 3'},
      ],
      // 供应商名称
      options2: {
        1: [
          {value: 'a', label: 'Option 1-1'},
          {value: 'b', label: 'Option 1-2'},
          {value: 'c', label: 'Option 1-3'}
        ],
        2: [
          {value: 'd', label: 'Option 2-1'},
          {value: 'e', label: 'Option 2-2'},
          {value: 'f', label: 'Option 2-3'}
        ],
        3: [
          {value: 'g', label: 'Option 3-1'},
          {value: 'h', label: 'Option 3-2'},
          {value: 'i', label: 'Option 3-3'}
        ]
      },
      // 子组号
      options3: {
        1: [
          {value: 'a1', label: '1111111'},
          {value: 'b1', label: '1111112'},
          {value: 'c1', label: '1111113'}
        ],
        2: [
          {value: 'd1', label: '2111111'},
          {value: 'e1', label: '2111112'},
          {value: 'f1', label: '2111113'}
        ],
        3: [
          {value: 'g1', label: '3111111'},
          {value: 'h1', label: '3111112'},
          {value: 'i1', label: '3111113'}
        ]
      },
      /* 日期选择器模块*/
      //
      pickerOptions: {
        disabledDate(time) {
          return time.getTime() > Date.now();
        },
        shortcuts: [{
          text: '今天',
          onClick(picker) {
            picker.$emit('pick', new Date());
          }
        }, {
          text: '昨天',
          onClick(picker) {
            const date = new Date();
            date.setTime(date.getTime() - 3600 * 1000 * 24);
            picker.$emit('pick', date);
          }
        }, {
          text: '一周前',
          onClick(picker) {
            const date = new Date();
            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
            picker.$emit('pick', date);
          }
        }]
      },
      options4: {
        value1: '',
        value2: '',
        value3: '',
        value4: '',
      },
    };
  }

}
</script>

<style scoped>
.el-header, .el-footer {
  background-color: #6ee1d4;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #D3DCE6;
  color: #333;
  text-align: center;
}

.el-main {
  background-color: #ffffff;
  color: #333;
  text-align: center;
  position: relative;
//line-height: 160px;
}

body > .el-container {
  margin-bottom: 20px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}

.el-row {
  margin-bottom: 10px;

  &:last-child {
    margin-bottom: 0;
  }
}

.el-col {
  border-radius: 4px;
  position: relative;
  text-align: left;
}

.bg-purple-dark {
  background: #ffffff;
}

.bg-purple {
  background: #ffffff;
}

.bg-purple-light {
  background: #ffffff;
}

.grid-content {
  border-radius: 4px;
  min-height: 36px;
}

.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>
