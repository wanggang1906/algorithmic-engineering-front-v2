<template>
  <div>
    <el-card class="box-card">
      <div>
        <span>卡片区</span>
        <!-- 手动上传 -->
        <el-upload
          :action="imageUploadUrl"
          :on-preview="handlePreview"
          :on-remove="handleRemove"
          :before-remove="beforeRemove"
          :limit="3"
          :on-exceed="handleExceed"
          :file-list="fileList"
          :auto-upload="false"
        >
          <el-button slot="trigger" size="small" type="primary">选取文件</el-button>
          <el-button style="margin-left: 10px;" size="small" type="success" @click="submitUpload">上传到服务器</el-button>
          <div slot="tip" class="el-upload__tip">只能上传jpg/png文件,只能传一个图片，且不超过500kb</div>
        </el-upload>
      </div>
    </el-card>

    <div>
      <el-card class="box-card">
        <div style="color: #666;font-size: 13px;">
          <svg-icon icon-class="system" style="margin-right: 5px" />
          <span>
            系统
          </span>
          <span>
            IP
          </span>
          <span>
            项目已不间断运行
          </span>
        </div>
      </el-card>
    </div>
    <div>
      <el-row>
        <el-col>
          <el-card class="box-card">
            <div style="color: #666;font-size: 13px;">
              <span>
                系统
              </span>
            </div>
          </el-card>
        </el-col>
        <el-col>
          <el-card class="box-card">
            <div style="color: #666;font-size: 13px;">
              <span>
                项目已不间断运行
              </span>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Image',
  data() {
    return {
      fileList: [],
      imageUploadUrl: 'url'

    }
  },
  methods: {
    // 删除
    handleRemove(file, fileList) {
      console.log(file, fileList)
    },
    // 预览
    handlePreview(file) {
      console.log(file)
    },
    // 选择超出处理
    handleExceed(files, fileList) {
      this.$message.warning(`当前限制选择 3 个文件，本次选择了 ${files.length} 个文件，共选择了 ${files.length + fileList.length} 个文件`)
    },
    beforeRemove(file, fileList) {
      return this.$confirm(`确定移除 ${file.name}？`)
    },
    // 处理上传
    submitUpload() {
      console.log('处理上传')
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
    /* rel关联到一个样式表，
    使用scss语法 */
    .clearfix:before,
    .clearfix:after {
        display: table;
        content: "";
    }
    .clearfix:after {
        clear: both;
    }
    // 卡片样式
    // deep深度作用选择器
    // 将全局的组件或者类的样式转换为局部的类从而达到在scoped内部添加样式后起作用的目的
    /deep/ .box-card {
        margin-bottom: 5px;
        width: 90%;
    span {
        margin-right: 28px;
    }
    .el-icon-refresh {
        margin-right: 10px;
        float: right;
        cursor:pointer;
    }
    }
    .el-upload {
        color: #666
    }

</style>
