<template>
  <div>
    <Herder></Herder>
   
    <nuxt /> <!-- nuxt相当于： <router-view></router-view> -->
     <Footer></Footer>
  </div>
</template>



<script>
import Herder from '@/components/header'
import Footer from '@/components/footer'

export default {
   components:{
     Herder,Footer
   }
}
</script>


<style lang='less'>

*{
  margin:0; 
  padding:0;
  box-sizing: border-box;
}
ul, li, ol{
  list-style:none;
}
a{
  text-decoration:none;
  //继承父类颜色
  color:inherit;
}
em,i{
  // 让这个字体正常  平常斜体的
  font-style: normal;
}


html {
  // 所有的页面都会经过这个文件 相当于app
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
</style>
