<template>
  <div id="app">
    <vheader :seller="seller"></vheader>
   <tab></tab>
   <keep-alive>
    <router-view :seller="seller"></router-view>
  </keep-alive>
  </div>
</template>

<script>
  import vheader from 'components/header/header'
  import tab from 'components/tab/tab'
  import axios from 'axios'
  import {urlParse} from 'common/js/util'
  const ERR_OK = 0

export default {
    data() {
      return {  /* 商家默认有id */
        seller: {
          id: (() => {  /* 从地址栏中的url中通过urlParam函数解析，得到id */
            let queryParm = urlParse()
            console.log(queryParm)
            return queryParm.id
          })()
        }
      }
    },
    created() {
        axios.get('/api/seller', {
          params: {
            ID: this.seller.id
          }
        }).then((res) => {
          res = res.data
        if (res.errno === ERR_OK) {
           /* 防止把id覆盖掉，使用es6的一个语法:扩展了对象的属性，在原来的基础上添加response.data的值，不会覆盖掉原来的id属性 */
          this.seller = Object.assign({}, this.seller, res.data)
          console.log(this.seller.id)
        }
      })
    },
  components: {
    vheader,
    tab
  }
}
</script>

<style scoped lang="scss">


</style>
