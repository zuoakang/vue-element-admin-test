<template>
  <div class="main-content">
    <div style="width: 90%; margin: 20px auto">
      <div class="sub-title-head">
        <div class="l-box" />
        {{ type === "detail" ? "耗材预申请 - 预申请详情" : "耗材预申请 - 222" }}
      </div>

      <h4>基本信息</h4>
      <div class="like-table-item">
        <div class="table-item">
          申请单号 <span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          出库单号 <span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          状态 <span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          申请部门 <span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          申请人 <span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          申请时间<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          使用时间<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          申请理由<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          审核人<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          审核时间<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          审核建议<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          出库人<span>{{ form.fixNo }}</span>
        </div>
        <div class="table-item">
          出库时间<span>{{ form.fixNo }}</span>
        </div>
      </div>
      <el-table
        ref="multipleTable"
        :data="tableData2"
        tooltip-effect="dark"
        style="width: 100%; margin: 55px 0"
      >
        <el-table-column type="index" width="55" />
        <el-table-column label="耗材图片">
          <template slot-scope="scope">
            <div slot="reference" class="name-wrapper">
              <img :src="scope.row.img" style="width: 100px">
            </div>
          </template>
        </el-table-column>
        <el-table-column prop="name" label="耗材编号" />
        <el-table-column prop="address" label="耗材名称" />
        <el-table-column prop="address" label="耗材类型" />
        <el-table-column prop="address" label="单位" />
        <el-table-column prop="address" label="申请数量" />
        <el-table-column prop="address" label="出库数量" />
      </el-table>

      <h4>申请进度</h4>
      <el-steps v-if="type === 'detail'" :active="2" style="padding: 55x 0">
        <el-step title="提交申请" icon="el-icon-success" />
        <el-step title="确认中" icon="el-icon-success" />
        <el-step title="采购出库" icon="el-icon-success" />
        <el-step title="发放" icon="el-icon-success" />
      </el-steps>
      <el-steps v-else :active="6" style="padding: 55x 0">
        <el-step title="提交申请" icon="el-icon-success" />
        <el-step title="确认中" icon="el-icon-success" />
        <el-step title="审核中" icon="el-icon-success" />
        <el-step title="审核通过" icon="el-icon-success" />
        <el-step title="采购出库中" icon="el-icon-success" />
        <el-step title="发放" icon="el-icon-success" />
      </el-steps>
      <div style="padding-top: 35px">
        <el-button @click="back">返回</el-button>
        <el-button
          v-if="type === 'check'"
          type="primary"
          @click="back"
        >确定签收</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      type: this.$route.params.type,
      headers: [
        {
          prop: 'date',
          label: '申请单号'
        },
        {
          prop: 'name',
          label: '申请部门'
        },
        {
          prop: 'address',
          label: '使用时间'
        },
        {
          prop: 'people',
          label: '审核人'
        }
      ],
      tableData2: [{
        date: '2016-05-03',
        name: '王小虎',
        address: '1518 弄',
        img: require('../../../assets/img/default.svg')
      }],
      textarea: '',
      selected: [],
      form: {
        fixNo: ''
      }
    }
  },
  computed: {
    getHeaders() {
      return this.tableData.reduce((pre, cur, index) => pre.concat(`value${index}`), ['title'])
    },
    getValues() {
      return this.headers.map(item => {
        return this.tableData.reduce((pre, cur, index) => Object.assign(pre, { ['value' + index]: cur[item.prop] }), { 'title': item.label })
      })
    }
  },
  methods: {
    back() {
      this.$router.go(-1)
    }
  }
}
</script>

<style lang="scss" scoped>
.m50 {
  margin: 50px;
}
.el-steps--horizontal {
  padding: 50px 0;
}
</style>
