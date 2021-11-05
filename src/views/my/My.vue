 
<template>
    <div>
         <img class="headerimg" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.jj20.com%2Fup%2Fallimg%2F1113%2F050320123144%2F200503123144-1-1200.jpg&refer=http%3A%2F%2Fimg.jj20.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1637226588&t=e8bf40765777eab75916fd9b3bd10ede" alt="">
        <ul>
            <li v-for="item in minearry" class="mineitem"
                @click="itemclick(item)" :key="item.label">
                <span class="minetitle">{{item.label}}</span>
                <i class="iconfont cubeic-arrow">&#xe65f;</i>
            </li>
        </ul>
    </div>
    <Docker/>
</template>
<script>
import Docker from '../home/Docker.vue'
export default {
  components: { Docker },
    data(){
        return{
            minearry:[
                {label:'商品收藏'},
                {label:'我的足迹'},
                {label:'店铺收藏'},
                {label:'我的订单',type:'order'},
                {label:'退出',type:'exit'},
            ]
        }
    },
    methods:{
        itemclick(item){
            if(item.type=='exit'){
                localStorage.removeItem('isLogin')
                this.$router.push({path:'/login'})
            }
            if(item.type=="order"){
                this.$router.push({path:'/order'})
            }
        }
    }
}
</script>
<style lang="scss" scoped>
.mineitem{
    font-size: 14px;
    text-align: left;
    height:50px;
    line-height:50px;
    padding-left:5%;
    border-bottom:1px solid #eee;
}
.minetitle{
    display: inline-block;

    width :90%
}
.headerimg{
    height :1.5rem;
    width :100%
}
</style>