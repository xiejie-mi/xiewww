<template>
    <div>
    <el-carousel :interval="5000" arrow="always">
        <el-carousel-item v-for="item in arr" :key="item" >
            <router-link :to="'list'+item.List"><img :src="item.img" style="width: 60%;height: 100%" alt=""></router-link>
        </el-carousel-item>
    </el-carousel>
    </div>
</template>
<script>
    export default {
        name: "Imagep",
        data(){
            return {
                msg:'Image',
                arr:[]
            }
        },
        created() {
            // 为给定 ID 的 user 创建请求
            var _this =this;
            this.$axios.get('/api/api/login')
                .then(function (response) {
                    console.log(response.data);
                    _this.arr=response.data
                })
                .catch(function (error) {
                    console.log(error);
                });
        }
    }

</script>

<style>
    .el-carousel__item h3 {
        color: #475669;
        font-size: 18px;
        opacity: 0.75;
        line-height: 300px;
        margin: 0;
    }

    .el-carousel__item:nth-child(2n) {
        background-color: #99a9bf;
    }

    .el-carousel__item:nth-child(2n+1) {
        background-color: #d3dce6;
    }
</style>