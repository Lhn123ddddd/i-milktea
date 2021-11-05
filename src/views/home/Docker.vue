<template>
  <div class="docker">
    <!-- item就是遍历的内容 index就是索引 
         :动态class
         'docker__item':true, 默认展示这个类名
         'docker__item--active':index===0 下标为0的时候有样式
    -->  
    <div 
    class="docker__item" v-for= "item in dockerList"
    :key= "item.icon
    ">
      <router-link :to="item.link" >
      <div class="iconfont" v-html="item.icon"></div>
      <div class="docker__title">{{item.text}}</div>
      </router-link>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Docker',
  setup(){
    //声明数组
    const dockerList = [
      {'icon':'&#xe6cb;',text:'首页',link:'/'},
      {'icon':'&#xe897;',text:'订单',link:'/Order'},
      {'icon':'&#xe62f;',text:'我的',link:'/My'},
    ];
    //数组导出
    return {dockerList};
  }
}
</script>

<style lang="scss">
@import '../../style/viriables.scss';
.docker {
  display: flex;
  box-sizing: border-box;
  position: fixed;
  padding: 0 .18rem;
  // padding-top:.4rem ;
  left: 0;
  bottom: 0;
  width: 100%;
  height: .49rem;
  // border-top: .01rem solid $content-bgColor;
  color: $content-fontcolor;
  background: white;
  a{
    text-decoration: none;
  }

  &__item {
    flex: 1;
    text-align: center;
    color: yellow;
    .iconfont {
      margin: .07rem 0 .02rem 0;
      font-size: .18rem;
    }
  }
  &__title {
    font-size: .2rem;
    transform: scale(.5, .5);
    transform-origin: center top;
  }
}
</style>