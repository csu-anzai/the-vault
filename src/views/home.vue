<template>
  <section class="home-page-container">
    <section class="content-wrapper-center-vertical fully-mtd">
      <div>
        <h1 id="dash-title" v-html="title"></h1>
      </div>
      <div>
        <span v-html="subTitle" style="font-size: 16px;"></span><span id="blog-entry">[ GO <a-icon type="swap-right" /> ]</span>
      </div>
    </section>
  </section>
</template>

<script>
import { setInterval, clearInterval } from 'timers';
export default {
  data() {
    return {
      title: '',
      subTitle: '',
    }
  },
  created() {
    this.loadingTitle()
  },
  methods: {
    init(){

    },
    loadingTitle() {
      let subTitle_tail = {
        execute: params => {
          this.subTitle = params
        },
        params: "The Management of Knowledge <b>V</b>ault"
      }
      let title = "{ V }"
      let subTitle = "The Management of Knowledge Vault"
      this.titleRender(title, 'title', 150)
      this.titleRender(subTitle, 'subTitle', 30, subTitle_tail)
    },
    titleRender(title, dataName, duration, tail) {
      let i = 0
      let interval = setInterval(() => {
        if(i == title.length) {
          clearInterval(interval)
          if(tail){
            tail.execute(tail.params)
          }
        }else{
          this[dataName] += title.charAt(i++)
        }
      }, duration)
    },
    go() {
      console.log('give it a go go...')
    }
  },
  
}
</script>

<style lang="scss" scoped>
  .home-page-container {
    width: 100%;
    height: 100%;
    background-color: #fff;
  }
  #dash-title {
    font-size: 80px;
    margin-bottom: 4px;
  }
  #blog-entry{
    margin-left: 10px;
    font-size: 18px;
    font-weight: bold;
    color: rgb(25, 202, 172) ;
  }
</style>