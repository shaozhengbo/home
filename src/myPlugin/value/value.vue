<template>
  <div>
    <el-row>
      <el-col :span="24">
        <span v-if="type === '0'">
          {{ value }}
        </span>
        <span v-if="type === '1'">
          <el-image
            style="width: 100px; height: 100px"
            :src="value"
            fit="cover"></el-image>
        </span>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "value",
  props: {
    /**
     * 显示类型
     * 0:文字，1：图片
     */
    type: {
      type: String,
      default: ''
    },
    /**
     * 后端接口参数
     */
    searchKey: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      value: ''
    }
  },
  mounted() {
    this.axios.get('/' + this.searchKey).then(res => {
      this.$message.success(res)
      this.value = Math.random() * 100
    }).catch(err => {
      this.value = Math.random() * 100
      this.$message.error(err)
    })
  }
}
</script>

<style scoped>

</style>
