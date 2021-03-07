<template>
  <div class="page">
      <div class="wrapper">
        <el-row>
            <el-col :xs="24" :sm="4" :md="18" :lg="18" :xl="18">
              <div class="main">
                <list_home :items="items"></list_home>
              </div>
            </el-col>
            <el-col :xs="0" :sm="4" :md="6" :lg="6" :xl="6">
              <div class="aside">
                <div class="card">
                  <p class="title">关于伊洛</p>
                  <img class="pic" src="../../static/img/p1.png" alt="">
                  <div class="row">
                    <p>人的天才只是火花，要使他变成熊熊火焰，那就只有学习！和继续学习 </p>
                    <div class="icons">
                      <a href="https://github.com/affection-beibei" target="_blank"><i class="iconfont icon-github"></i></a>
                        <!-- 知乎链接  -->
                      <!-- <a href="javascript:;" target="_blank"><i class="iconfont icon-zhihu"></i></a> -->
                      <a href="https://y.qq.com/n/yqq/playlist/5365470087.html#stat=y_new.profile.create_playlist.click&dirid=1" target="_blank"><i class="iconfont icon-yinle"></i></a>
                             <!-- 微博链接 暂时不考虑微博  -->
                      <!-- <a href="https://weibo.com/u/5746403289?refer_flag=1005055010_&is_all=1" target="_blank"><i class="iconfont icon-weibo"></i></a> -->
                    </div>
                  </div>
                </div>
                <div class="card">
                  <p class="title">技术分享</p>
                  <div class="row">
                    <a class="link" href="https://cn.vuejs.org/" target="_blank">Vue.js</a>|
                    <a class="link" href="https://reactjs.org/" target="_blank">React</a>|
                    <a class="link" href="https://juejin.im/" target="_blank">掘金</a>|
                    <a class="link" href="https://www.npmjs.com/" target="_blank">NPM</a>|
                    <a class="link" href="https://www.bilibili.com/" target="_blank">二次元专属</a>
                    <a class="link" href="https://ke.qq.com/" target="_blank">腾讯课堂</a>
                    <a class="link" href="https://ke.qq.com/" target="_blank">YouTube</a>
                    <a class="link" href="https://pan.baidu.com/s/1CjKoqIZrdDDSdItyM0wsBQ" target="_blank">谷歌翻墙工具</a>
                    <a href="javascript:;">提取码：e2m9</a>
                    <!-- 链接：https://pan.baidu.com/s/1CjKoqIZrdDDSdItyM0wsBQ  -->
                    <!--  -->
                  </div>
                </div>
              </div>
            </el-col>
        </el-row>
      </div>
  </div>
</template>

<script>
import List_home from "../components/list_home"
import {webUrl} from "../../static/js/public.js"
export default {
  data(){
    return{
      items:[]
    }
  },
  components:{
    List_home,
  },
  created(){
    this.$axios.post(webUrl+'articleList')
      .then((res)=>{
        this.items=res.data.reverse();
      })
  }
}
</script>

<style lang="scss" scoped>
.main{
  background: #f8f8fd;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.4), 0 0 30px rgba(10, 10, 0, 0.1) inset;
  margin:0 10px;
  padding: 10px;
}
.aside{
  background: #f8f8fd;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.4), 0 0 30px rgba(10, 10, 0, 0.1) inset;
  .card{
    border-top: 1px solid #eee;
    .title{
      padding: 10px;
      font-weight: 600;
      color:#808080;
      margin-bottom: 10px;
    }
    .pic{
      width: 100%;
    }
    .row{
      padding: 0 10px;
      &>p{
        color:#bfbfbf;
        
      }
      .icons{
        padding:10px 0;
        .iconfont{
          transition: all .3s;
          margin: 5px;
          color: #000;
          font-size: 20px;
          background-color: rgba(200, 200, 200, 0.3);
          padding: 8px;
          border-radius: 50%;
          &:hover{            
            color:#fff;
            background-color: rgba(0, 133, 166, 0.8);
            border-radius: 5px;          
          }
        }
      }

      &>.link{
        color:#bfbfbf;
        display: inline-block;
        padding: 5px;
        transition: all .3s;        
        &:hover{
          color: #0085a1;
        }
      }
    }
  }
}

@media (min-width: 768px) {//pc
  .main{
    margin:0 20px;
    padding: 20px;
  }
}
</style>
