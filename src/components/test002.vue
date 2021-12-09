<template>
  <div>
    <el-row type="flex" class="row-bg" justify="center">
      <!-- 左侧-content -->
      <div style="margin-right: 15px">
        <h1 align="left">Employee setting</h1>
        <!-- 搜索条件 -->
        <el-row type="flex" class="row-bg">
          <el-input
            v-model="search"
            style="width: 100%"
            placeholder="请输入员工序号" @change@="searchHandler('1')"
          >
          </el-input>
          <el-button
            type="primary"
            style="margin-left: 5px"
            @click="searchHandler('1')"
            >search</el-button
          >
        </el-row>
        <!-- 表格部分 -->
        <el-table
          :data="leftDataTable"
          height="450"
          border
          highlight-current-row
          style="width: 100%"
          ref="table"
          key="one"
        >
          <el-table-column
            key="selection"
            prop="selection"
            label="selection"
            type="selection"
            width="100"
          >
          </el-table-column>
          <el-table-column key="aa" prop="aa" label="序号" width="100">
          </el-table-column>
          <el-table-column key="date" prop="date" label="日期" width="100">
          </el-table-column>
          <el-table-column prop="name" label="姓名" width="100">
          </el-table-column>
          <el-table-column key="address" prop="address" label="地址">
          </el-table-column>
        </el-table>
      </div>
      <!-- 右侧-content -->
      <div>
        <h1 align="left">Employee setting</h1>
        <!-- 搜索条件 -->
        <el-row type="flex" class="row-bg">
          <el-input
            v-model="search5"
            style="width: 100%"
            placeholder="请输入员工序号"
          >
          </el-input>

          <el-button
            type="primary"
            style="margin-left: 5px"
            @click="searchHandler('2')"
            >search5</el-button
          >
        </el-row>
        <!-- 表格部分 -->
        <el-table
          :data="tableData5"
          height="450"
          border
          highlight-current-row
          style="width: 100%"
          key="two"
          ref="multipleTable"
        >
          <el-table-column
            key="selection"
            prop="selection1"
            label="selection"
            type="selection"
            width="100"
          >
          </el-table-column>
          <el-table-column key="aa" prop="aa" label="序号" width="100">
          </el-table-column>
          <el-table-column key="date" prop="date" label="日期" width="100">
          </el-table-column>
          <el-table-column prop="name" label="姓名" width="100">
          </el-table-column>
          <el-table-column key="address" prop="address" label="地址">
          </el-table-column>
        </el-table>
      </div>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: "", // 左侧搜索条件
      search5: "", // 右侧搜索条件
      // 左侧表格数据-展示格式如下
      leftDataTable: [
        // {
        //   checked: true,     //勾选
        //   aa: "001",         //序号
        //   date: "2016-05-03",//日期
        //   name: "亚瑟-y",    //姓名
        //   address: "北京",   //地址
        // }。。。。
      ],
      // 右侧表格数据-展示格式如下
      tableData5: [
        // {
        //   aa: "006",
        //   date: "2016-05-06",
        //   name: "hello",
        //   address: "上海市普陀区金沙江路 1518 弄",
        // },
      ],
    };
  },
  mounted() {
    /**
     * !如果点击搜索时不改变初始选中状态，则注释掉347行即可
     */
    this.getInitLeftData(); // 初始化请求接口-左侧
    this.getInitRightData(); // 初始化请求接口-右侧
  },
  methods: {
    // 加载接口获取数据-左侧
    getInitLeftData() {
      // 左侧请求回来的数据 （目前假数据：接口数据有赋值即可）
      const apiData = [
        {
          checked: true, //勾选
          aa: "001", //序号
          date: "2016-05-03", //日期
          name: "亚瑟-y", //姓名
          address: "北京", //地址
        },
        {
          checked: true,
          aa: "002",
          date: "2016-05-02",
          name: "鲁班-l",
          address: "上海市",
        },
        {
          checked: true,
          aa: "003",
          date: "2016-05-04",
          name: "米莱迪-m",
          address: "天津",
        },
        {
          checked: true,
          aa: "004",
          date: "2016-05-01",
          name: "妲己-d",
          address: "海南",
        },
        {
          checked: true,
          aa: "005",
          date: "2016-05-08",
          name: "孙尚香-s",
          address: "四川",
        },
        {
          checked: false,
          aa: "006",
          date: "2016-05-06",
          name: "公孙离-g",
          address: "湖南",
        },
        {
          checked: false,
          aa: "007",
          date: "2016-05-07",
          name: "蒙犽-m",
          address: "黑龙江",
        },
        {
          checked: false,
          aa: "008",
          date: "2016-05-10",
          name: "夏侯惇-x",
          address: "吉林",
        },
        {
          checked: false,
          aa: "009",
          date: "2016-05-02",
          name: "陈咬金-c",
          address: "云南",
        },
        {
          checked: false,
          aa: "010",
          date: "2016-05-05",
          name: "吕布-l",
          address: "江苏",
        },
        {
          checked: false,
          aa: "011",
          date: "2016-05-09",
          name: "貂蝉-d",
          address: "上海市",
        },
      ];
      this.leftDataTable = this.initSortData(apiData); // 初始排序
      this.setChecked(this.leftDataTable, "table"); // 设置勾选效果
    },
    // 加载接口获取数据-右侧
    getInitRightData() {
      // 左侧请求回来的数据 （目前假数据：接口数据有赋值即可）
      const apiData = [
        {
          checked: true, //勾选
          aa: "001", //序号
          date: "2016-05-03", //日期
          name: "张三", //姓名
          address: "北京", //地址
        },
        {
          checked: true,
          aa: "002",
          date: "2016-05-02",
          name: "李四",
          address: "上海市",
        },
        {
          checked: true,
          aa: "003",
          date: "2016-05-04",
          name: "王五",
          address: "天津",
        },
        {
          checked: true,
          aa: "004",
          date: "2016-05-01",
          name: "史莱克",
          address: "海南",
        },
        {
          checked: true,
          aa: "005",
          date: "2016-05-08",
          name: "戴沐白",
          address: "四川",
        },
        {
          checked: false,
          aa: "006",
          date: "2016-05-06",
          name: "刘备",
          address: "湖南",
        },
        {
          checked: false,
          aa: "007",
          date: "2016-05-07",
          name: "齐白石",
          address: "黑龙江",
        },
        {
          checked: false,
          aa: "008",
          date: "2016-05-10",
          name: "夏侯惇",
          address: "吉林",
        },
        {
          checked: false,
          aa: "009",
          date: "2016-05-02",
          name: "陈咬金",
          address: "云南",
        },
        {
          // checked: false,
          aa: "010",
          date: "2016-05-05",
          name: "刘欢",
          address: "江苏",
        },
        {
          checked: false,
          aa: "011",
          date: "2016-05-09",
          name: "貂蝉",
          address: "上海市",
        },
      ];
      this.tableData5 = this.initSortData(apiData); // 初始排序
      this.setChecked(this.tableData5, "multipleTable"); // 设置勾选效果
    },
    // 排序函数
    initSortData(arr, key = "name") {
      if (Array.isArray(arr) && arr.length) {
        let newArr = arr.sort((a, b) => a[key].localeCompare(b[key], "zh")); //a~z 排序
        let arr1 = []; // 未选中集合
        let arr2 = []; // 选中集合
        newArr.forEach((item, index) => {
          !item.checked ? arr1.push(item) : arr2.push(item);
        });
        return [...arr1, ...arr2]; //汇集总数据
      }
      return [];
    },
    /**
     * @description: 设置表格勾选效果
     * @param {*} arr 表格数据
     * @param {*} key 当前表格ref值
     */
    setChecked(arr, key) {
      if (Array.isArray(arr) && arr.length) {
        this.$nextTick(() => {
          arr.forEach((item, index) => {
            if (item.checked) {
              this.$refs[key].toggleRowSelection(item, true);
              this.$refs[key].setCurrentRow(item);
            }
          });
        });
      }
    },

    /**
     * @description:  搜索按钮事件
     * @param {*} curBtn 1：左侧点击 2：右侧点击
     */
    searchHandler(curBtn) {
      let arr = curBtn === "1" ? this.leftDataTable : this.tableData5; // 当前表格数据
      const key = curBtn === "1" ? "table" : "multipleTable"; //对应表格绑定ref的key值
      const value = curBtn === "1" ? this.search : this.search5; // 输入搜索条件
      const type = curBtn === "1" ? "1" : "1"; // 对应值搜索
      const indexArr = this.checkoutData(value, arr, type); // 得到可以选中的值（类型为数组）
      this.resetStatus(arr, key); // 清空状态:（如果注释掉此行，则不可变上次选中状态）
      if (indexArr.length) {
        // 勾选中
        indexArr.forEach((i) => {
          /*this.$refs[key].toggleRowSelection(arr[i], true);*/
          this.$refs[key].setCurrentRow(arr[i]);
        });
        this.toLocateScroll(key, indexArr[0]); // 定位到指定位置
      } else {
        // this.$message({
        //   message: "暂未查询到相应数据；请重新输入",
        //   type: "warning",
        // });
      }
    },
    // 恢复初始化状态
    resetStatus(arr, refKey) {
      if (Array.isArray(arr) && arr.length) {
        arr.forEach((item, index) => {
          /*this.$refs[refKey].toggleRowSelection(arr[index], false);去掉就不会把之前的对选购 */ 
        });
      }
    },
    /**
     * @param {*} value 搜索条件
     * @param {*} arr 数组
     * @param {*} type 1:值搜索 2：模糊搜索
     * @return {*} 满足条件的索引数组
     */
    checkoutData(value, arr, type = "1") {
      let obarr = [];
      if (typeof value === "string") value = value.trim();
      if (Array.isArray(arr) && arr.length) {
        arr.forEach((item, index) => {
          // 值对应才可搜索
          if (type == "1") {
            Object.keys(item).forEach((obKey) => {
              if (item[obKey] === value) {
                obarr.push(index);
              }
            });
          } else {
            // 模糊搜索
            for (const iterator of Object.values(item)) {
              if (String(iterator).indexOf(value) > -1) {
                obarr.push(index);
                break;
              }
            }
          }
        });
      }
      return obarr;
    },
    /**
     * @description: 定位到指定滚动位置（调用时采用异步即可）
     * @param {*} ref 当前表格绑定的ref值
     * @param {*} i 指定索引
     */
    toLocateScroll(key, i) {
      const ref = this.$refs[key];
      if (ref) {
        this.$nextTick(() => {
          const targetTop = ref.$el
            .querySelectorAll(".el-table__body tr")
            [i].getBoundingClientRect().top;
          const containerTop = ref.$el
            .querySelector(".el-table__body")
            .getBoundingClientRect().top;
          const scrollParent = ref.$el.querySelector(".el-table__body-wrapper");
          scrollParent.scrollTop = targetTop - containerTop;
        });
      }
    },
  },
};
</script>
