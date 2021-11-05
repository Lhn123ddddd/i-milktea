<template>
  <div class="orderitem">
    <div class="shop">
      <img :src="item.imgUrl" class="shop__img">
      <div class="shop__title">{{item.name}}</div>
    </div>
    <div 
        :class='{"shop__content":true,"shop__content--bordered":hideBorder?false:true}'
        >
        <div class="shop__content__goods">
          <img :src="item.goodUrl">
        </div>
        <div class="shop__content__tags">
          <span class="shop__content__tag">￥{{item.price}}</span>
          <span class="shop__content__tag">共{{item.count}}件</span>
          <span class="shop__content__tag">配送费:{{item.expressPrice}}</span>
        </div>
    </div>
    <div class="shop__bottom">
        <button>评价拿红包</button>
        <router-link :to="`/shop/${item._id}`">
        <button class="onemore">再来一单</button>
        </router-link>
    </div>
  </div>  
</template>
<script>
import { useStore } from 'vuex'
    export default{
        name:'OrderInfo',
        // 组件父传子
        props:['item','hideBorder'],
        setup(){
          const Store=useStore()
          const cartList=Store.state.cartList
          return{cartList}
        }
    }
    
</script>
<style scoped lang="scss">
@import '../style/viriables.scss';
.orderitem{
    padding: .1rem;
    border: 1px solid #dfdede;
    border-radius:.05rem ;
    margin-bottom: .06rem;
    background: white;
.shop {
    display: flex;
    padding-top: .12rem;
    &__title {
      line-height: .22rem;
      font-size: .14rem;
      color: $content-fontcolor;
    }
    &__img {
      margin-right: .1rem;
      width: .25rem;
      height: .25rem;
      border-radius: .05rem;
    }
}
  .shop__content {
    display: flex;
    &__goods{
        img{
             width: 0.6rem;
             height: 0.6rem;
             border-radius: .1rem;
        };
    }
    &--bordered{
        border-bottom: 1px solid $content-bgColor;
    }
    
    &__tags {
      margin-top: .08rem;
      line-height: .18rem;
      font-size: .13rem;
      color: $content-fontcolor;
    }
    &__tag {
      margin-right: .3rem;
    }
  }
.shop__bottom{
    height: .2rem;
    display: flex;
    justify-content: flex-end;
    width: 100%;
    button{
        line-height: .16rem;
        margin-right:.1rem ;
        color: rgb(75, 74, 74);
        border-radius:.2rem ;
        border: 1px solid #a5a4a4;
    }
    .onemore{
        float: right;
        border: 1px solid rgb(51, 188, 241);
        color: rgb(51, 188, 241);
        border-radius:.2rem ;
    }
    
}
}
</style>