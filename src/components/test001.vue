<template>
  <div>
    

   
      <h1 align="left">Employee setting</h1>
     <div>
      <el-input v-model="keywold" style="display: inline-block;width: 350px;
      padding: 14px 14px;font-size: 24px;float:left" 
        placeholder="请输入搜索内容"
        @change="setCurrentRow">
      </el-input>
     
      
       <el-button type="primary" style="display: inline-block;float:left"
       >search</el-button>
        </div>
   

<!--
   <p>
      选中第
      <el-select v-model="currentIndex" @change="setCurrentRow">
        <el-option
          v-for="i in tableData4.length"
          :key="i"
          :value="i"
          :label="i">
        </el-option>
      </el-select>
      行
    </p>-->



    <el-table :data="tableData3" height="250" border highlight-current-row style="width: 100%" ref="table">
      
   
    <el-table-column prop="selection" label="selection" type="selection" width="180">
    </el-table-column>



      <el-table-column prop="aa" label="序号" width="180">
         </el-table-column>
      <el-table-column prop="date" label="日期" width="180">
      </el-table-column>
      <el-table-column prop="name" label="姓名" width="180">
      </el-table-column>
      <el-table-column prop="address" label="地址">
      </el-table-column>
    </el-table>
   
 </div>
</template>

<script>

  export default{
  data() {
    return {
      tableData3: [{
        
        aa:'001',
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        aa:'002',
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'003',
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'004',
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'005',
        date: '2016-05-08',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'006',
        date: '2016-05-06',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'007',
        date: '2016-05-07',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      },{aa:'008',
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'009',
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {aa:'010',
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }
      
      
      
      ],
      keywold: '',
      
      
    }
  },
   


 
  methods: {
    
   
    setCurrentRow(i) {
      this.$refs.table.toggleRowSelection(this.tableData3[i-1],true);
            /*this.$refs.table.toggleRowSelection(this.tableData3[i-1],false);*/

      this.$refs.table.setCurrentRow(this.tableData3[i - 1])/**指定到哪一行 并且有颜色 */
      /*对选框和颜色全部被选中之后就可以排序在表格数据的最下方*/


      const targetTop = this.$refs.table.$el.querySelectorAll('.el-table__body tr')[i - 1].getBoundingClientRect().top
      const containerTop = this.$refs.table.$el.querySelector('.el-table__body').getBoundingClientRect().top
      const scrollParent = this.$refs.table.$el.querySelector('.el-table__body-wrapper')
      scrollParent.scrollTop = targetTop - containerTop
    }
  }
    


}
</script>


<style scoped lang="scss">

</style>
