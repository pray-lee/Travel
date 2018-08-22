<template>
   <div class="detail">
     <detail-banner></detail-banner>
     <detail-header></detail-header>
     <div class="content">
       <detail-list :list="list"></detail-list>
     </div>
   </div>
</template>

<script>
  import DetailBanner from './components/Banner'
  import DetailHeader from './components/Header'
  import DetailList from './components/List'
  export default {
    name: 'Detail',
    components: {
      DetailBanner,
      DetailHeader,
      DetailList
    },
    data () {
      return {
        list: [
          {
            title: '成人票',
            children: [
              {
                title: '成人票1级',
                children: [{
                  title: '成人票2级子菜单'
                }]
              },{
                title: '成人票2级'
              },{
                title: '成人票3级'
              }
            ]
          },{
            title: '学生票'
          },{
            title: '老年票'
          },{
            title: '特惠票'
          }
        ]
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .content
    height: 50rem
</style>
