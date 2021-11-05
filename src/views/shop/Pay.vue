<template>
    <div class="search">
            <div class="iconfont" @click= "handelBackClick">
                &#xe660;你的余额不足以支付，建议返回
            </div>
    </div>  
</template>
<script>
import {useRouter} from 'vue-router'
const useBackEffect = ()=>{
    const router = useRouter();
    const handelBackClick = ()=>{
        // 退回上一个
        router.back();
    }
    return handelBackClick
}
export default{
    name:'Pay',
    setup (){
        const handelBackClick = useBackEffect();
        return {handelBackClick}
    }
}
</script>
<style scoped lang="scss">
.search{
    display: flex;
    margin: .14rem 0 .1rem .14rem;
    line-height: .3rem;
    .iconfont{
        font-size: .2rem;
    }
}
</style>