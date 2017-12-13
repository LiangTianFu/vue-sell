<template>
  <div id="tab">
   <div class="tab border-1px">
        <router-link tag="div" class="tab-item" to="/goods">
            <span class="tab-link">商品</span>
        </router-link>
        <router-link tag="div" class="tab-item" to="/ratings">
            <span class="tab-link">评论</span>
        </router-link>
        <router-link tag="div" class="tab-item" to="/seller">
            <span class="tab-link">商家</span>
        </router-link>
   </div>
   </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
@import "~common/scss/mixin.scss";

.tab {
    display: flex;
    width: 100%;
    height: 40px;   /* 移动端的大小是两倍的,不能写80px */
    line-height: 40px;
    @include border-1px(rgba(7,17,27,0.1));
    .tab-item {
        flex: 1;
        text-align: center;
        .tab-link {
            font-size: 14px;
            color: rgb(77,85,93);
        }
        &.router-link-active {
            .tab-link {
                color:rgb(240,20,20);
            }
        }
    }
}

</style>
