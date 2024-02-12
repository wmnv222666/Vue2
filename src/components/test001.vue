    <template>
    <div class="table-data-section">
      <div class="table">
        <el-table :data="invoicesHistoryList" v-loading="tableLoading" height="100%" style="width: 95%" border stripe>
          <el-table-column
            prop="invoiceNo"
            :label="'Invoice Number'"
            align="center"
            header-align="center"
            min-width="12%"
          >
          </el-table-column>

          <el-table-column
            prop="invoiceComments"
            :label="'Invoice Comments'"
            align="center"
            header-align="center"
            min-width="14%"
            :show-overflow-tooltip="true"
          >
          </el-table-column>
          <el-table-column
            prop="invoiceCreateDate"
            :label="'Date'"
            align="center"
            header-align="center"
            min-width="8%"
          >
          </el-table-column>
          <el-table-column prop="companyName" :label="'Issuer'" align="center" header-align="center" min-width="12%">
          </el-table-column>        
          <el-table-column prop="totalFee" :label="'Total'" align="center" header-align="center" min-width="5%">
          </el-table-column>
          <el-table-column prop="invoiceType" :label="'Type'" align="center" header-align="center" min-width="10%">
          </el-table-column>
          <el-table-column
            prop="invoiceUploadDate"
            :label="'Upload Date'"
            align="center"
            header-align="center"
            min-width="8%"
          >
          </el-table-column>
          <el-table-column prop="brFlag" :label="'BR'" align="center" header-align="center" min-width="6%">
            <template slot-scope="scope">
              <span class="br-icon-class">
                <a-icon v-if="scope.row.brFlag" class="br-icon_success" type="check-circle" />
                <a-icon v-else class="br-icon_fail" type="close-circle" />
              </span>
            </template>
          </el-table-column>
       

        </el-table>
      </div>
      
  
    </div>
    </template>
    <script>
    export default {
  data() {
    return {}
  }
    }
    
     
</script>