<template>
    <div class="wrapper">
    <div class="top">
        <div class="top__bar">全部</div>
        <div class="top__bar">待消费</div>
        <div class="top__bar">待评价</div>
        <div class="top__bar">退款</div>
    </div>
        <OrderInfo v-for='data in item' :key='data._id'
        :item="data"
        :hideBorder="true"/>
        <!-- <OrderInfo/> -->
    </div>
    <Docker/>
</template>
<script>
import Docker from '../home/Docker'
import {useRoute} from 'vue-router'
import OrderInfo from '../../components/OrderInfo'
import {reactive,toRefs} from 'vue'
import {get} from '../../untils/request'
const useOrderInfoEffect = ()=>{
    const route = useRoute();
    const data = reactive({item:{}});
    const getItemData = async ()=>{
        // console.log(`${route.params.id}`);
        // 发送请求
        const result = await get(`/api/order/${route.params.id}`);
        // console.log(result);
        if(result.errno == 0 && result.data){
            // console.log(result.data);
            data.item = result.data;
        }
    }
    const {item} = toRefs(data);
    return {item,getItemData};
}
export default {
    name:'Order',
    components:{ Docker,OrderInfo },
    setup(){
        // 函数的执行流程
        const {item,getItemData} = useOrderInfoEffect();
        getItemData();
        return {item}
    }
}
</script>
<style scoped lang="scss">
.top{
    width: 100%;
    position:fixed;
    top:0;
    background: rgb(245, 243, 243);
    &__bar{
        height: .3rem;
        padding-bottom: .01rem;
        margin-top: .1rem;
        margin-right: .2rem;
        float: left;
        font-size:.18rem ;
    }
}
.wrapper{
        position: relative;
        background: rgb(245, 243, 243);
        padding:0.4rem .18rem .5rem .18rem;

}
</style>