<template>
    <div>
      111111111
      <div class="block">
        <span class="demonstration">完整功能</span>
        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="currentPage"
          :page-sizes="[100, 200, 300, 400]"
          :page-size="limit"
          layout="total, sizes, prev, pager, next, jumper"
          :total="400">
        </el-pagination>
      </div>
      <el-input v-model="word"></el-input>
      <el-button @click="search">搜索</el-button>
    </div>
</template>

<script>
    export default {
        name: "example",
      inject:['replace'],
      data(){
          return{
            currentPage:1,
            limit:100,
            word:''
          }
        },
        methods:{
          handleSizeChange(val) {
            console.log(`每页 ${val} 条`);
            this.replace('limit',val)
          },
          handleCurrentChange(val) {
            this.replace('page',val)
          },
          search(){
            this.replace('word',this.word)
          }
        },
      created() {
          console.log(this.$route)
        this.currentPage=this.$route.query.page*1;
          this.limit=this.$route.query.limit*1;
      }
    }
</script>

<style scoped>

</style>
