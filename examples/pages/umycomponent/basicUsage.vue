<template>
  <div>
    <h3>基础表格</h3>
    <p>当u-table元素中注入data对象数组后，在u-table-column中用prop属性来对应对象中的键名即可填入数据，用label属性来定义表格的列名。可以使用width属性来定义列宽。</p>
    <u-table
      :data="tableData"
      :border="false"
      style="width: 100%">
      <template slot="empty">
        没有查询到符合条件的记录
      </template>
      <u-table-column
        prop="name"
        label="名字"
        width="180">
      </u-table-column>
      <u-table-column
        prop="sex"
        label="性别"
        width="180">
      </u-table-column>
      <u-table-column
        prop="age"
        label="年龄">
        <template v-slot="scope">
          <el-select v-model="scope.row.sex">
            <el-option v-for="item in sexList" :key="item.value" :label="item.label" :value="item.value"></el-option>
          </el-select>
        </template>
      </u-table-column>
    </u-table>
    <div v-html="md" style="margin-top: 30px" class="width100"></div>
    <h3>带斑马纹表格</h3>
    <p>使用带斑马纹的表格，可以更容易区分出不同行的数据。</p>
    <p>`stripe`属性可以创建带斑马纹的表格。它接受一个`Boolean`，默认为`false`，设置为`true`即为启用。</p>
    <u-table
      :data="tableData2"
      :border="true"
      stripe
      style="width: 100%">
      <u-table-column
        prop="name"
        label="名字"
        width="180">
      </u-table-column>
      <u-table-column
        prop="sex"
        label="性别"
        width="180">
      </u-table-column>
      <u-table-column
        prop="age"
        label="年龄">
      </u-table-column>
    </u-table>
    <div v-html="md2" style="margin-top: 30px" class="width100"></div>
  </div>
</template>
<script>
  import basicUsage from '../../components/u-table-component/basicTableUsage/basicUsage.md'
  import basicUsage2 from '../../components/u-table-component/basicTableUsage/basicUsage2.md'
  export default {
    data() {
      return {
        sexList: [
          { value: 1,label: '男' },
          { value: 2,label: '女'},
          { value: 3,label: '未知'}
        ],
        tableData: [{
          sex: '男',
          name: '王小虎',
          age: '15'
        }, {
          sex: '女',
          name: '王小明',
          age: '15'
        }, {
          sex: '女',
          name: '王小丽',
          age: '15'
        }, {
          sex: '未知',
          name: '王小狗',
          age: '15'
        }],
        tableData2: [{
          sex: '男',
          name: '王小虎',
          age: '15'
        }, {
          sex: '女',
          name: '王小明',
          age: '15'
        }, {
          sex: '女',
          name: '王小丽',
          age: '15'
        }, {
          sex: '未知',
          name: '王小狗',
          age: '15'
        }]
      }
    },
    computed: {
      md () {
        return basicUsage
      },
      md2 () {
        return basicUsage2
      }
    }
  };
</script>
