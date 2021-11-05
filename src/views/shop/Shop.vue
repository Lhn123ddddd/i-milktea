<template>
    <div class="wrapper">
        <div class="search">
            <div class="iconfont" @click="handelBackClick">
                &#xe660;
            </div>
            <div class="search__content">
                <span class="iconfont">&#xe600;</span>
                <input type="text" placeholder="波霸奶茶">
            </div>
        </div>
        <ShopInfo 
            :item="item"
            :hideBorder="true"
        />
        <Content/>
        <Cart/>
    </div>    
        
</template>
<script>
import {reactive,toRefs} from 'vue'
import {useRoute,useRouter} from 'vue-router'
import ShopInfo from '../../components/ShopInfo'
import {get} from '../../untils/request'
import Content from './Content'
import Cart from './Cart'

//useRoute 和useRouter的区别
//跳转useRouter
//获取useRoute
//获取当前店铺的信息
const useShopInfoEffect = ()=>{
    const route = useRoute();
    const data = reactive({item:{}});
    const getItemData = async ()=>{
        // console.log(`${route.params.id}`);
        // 发送请求
        const result = await get(`/api/shop/${route.params.id}`);
        // console.log(result);
        if(result.errno == 0 && result.data){
            // console.log(result.data);
            data.item = result.data;
        }
    }
    const {item} = toRefs(data);
    return {item,getItemData};
}
//点击回退逻辑
const useBackEffect = ()=>{
    const router = useRouter();
    const handelBackClick = ()=>{
        // 退回上一个
        router.back();
    }
    return handelBackClick
}
export default{
    name:'Shop',
    components:{ShopInfo,Content,Cart},
    setup(){
        // 函数的执行流程
        const {item,getItemData} = useShopInfoEffect();
        const handelBackClick = useBackEffect();
        getItemData();
        return {item,handelBackClick}
    }
}
</script>

<style scoped lang="scss">
@import '../../style/viriables.scss';
    .wrapper{
        padding:0 0.18rem;
    }
    .search{
        display: flex;
        margin: .14rem 0 .1rem 0;
        line-height: .3rem;
        .iconfont{
            font-size: .2rem;
        }
        &__content{
            display: flex;
            flex:1;
        }
        input{
            width: 100%;
            border: 0;
            background:$content-bgColor;
            outline: none;
            border-radius: 0.16rem;
        }
    }
</style>