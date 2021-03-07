<template>
  <div class="page" id="page" @click="clickTips">
      <div class="wrapper">
        <el-row>
            <el-col :xs="24" :sm="4" :md="18" :lg="18" :xl="18">
              <div class="main">
                <p class="title">关于伊洛</p>
                <!-- <list_article :items="items" type="archives"></list_article> -->
                <div class="card">
                  <p class="card-title" id="anchor-about">自我介绍</p>
                  <p class="txt">本人是一名刚毕业的学生,喜欢看书，自学，看电影</p>
                  <p class="txt">当然我本人也是一位非常热爱美女的人，对于有想了解前端方面问题的女孩，我也会毫不吝啬的去解决</p>
                  <p class="txt"> 当然如果你是一位男生,那么十有八九我是不会理你的</p>
                  <p class="txt">对于此，我知道很多人看不习惯，但是你也拿我没办法，忍受着吧</p>
                </div>
                <div class="card">
                  <p class="card-title" id="anchor-contact">如何联系我？</p>
                  <ul>
                    <li @click="btn_link"> 个人主页：<a href="javascript:;" >一只小伊洛</a></li>  <!-- target="_blank"-->
                    <li>Github：<a href="https://github.com/affection-beibei" target="_blank">affection-beibei</a></li>
                    <li><a href="https://www.baidu.com" target="_blank">还有别的问题，我建议去百度，现在都是面向百度开发，点击我，走向百度成功之路</a></li>
                    <li><a href="https://y.qq.com/n/yqq/playlist/5365470087.html#stat=y_new.profile.create_playlist.click&dirid=1" target="_blank">QQ音乐</a></li>
                    <li>Email： <a href="mailto:1819220834@qq.com">1819220834@qq.com</a></li>
                    <li>QQ：3460923301</li>
                  </ul>
                </div>
                <div class="card">
                  <p class="card-title" id="anchor-us">关于本站</p>
                  <p class="txt">博客只为了分享自己的一些心得体会</p>
                  <p class="txt">这也是自己第一次做博客，希望和大家多多交流，一起成长！</p>
                  <p class="txt">欢迎大家提一些对于本博客的的建议</p>
                  <ul>
                    <li>如果你没有账号的话</li>
                    <li>可以自己注册一个，然后在上面发表留言等一些评论</li>
                    <li>而我相对应的也是可以看到你们发布的信息，注册后当然也是可以进行对应的文章发布，对于想要发布文章心得的小伙伴可以直接发我邮件，我会添加你的专属账号</li>
                    <li>而我，对于你们发布的修改信息，我可以选择不接受，气不气</li>
                    <li>-----------毕竟刚开始，初始目的只是为了自我学习的笔记收藏----------------</li>
                  </ul>
                </div>
                <div class="card">
                  <p class="card-title" id="anchor-friend">友情链接</p>
                  <div class="row-link">
                    <a class="link" href="https://cn.vuejs.org/" target="_blank">Vue.js</a>|
                    <a class="link" href="https://reactjs.org/" target="_blank">React</a>|
                    <a class="link" href="https://juejin.im/" target="_blank">掘金</a>|
                    <a class="link" href="https://www.npmjs.com/" target="_blank">NPM</a>|
                    <a class="link" href="https://www.bilibili.com/" target="_blank">二次元专属</a>
                  </div>
                </div>
              </div>
            </el-col>
            <el-col :xs="0" :sm="4" :md="6" :lg="6" :xl="6">
              <div class="aside">
                <p class="title">Content</p>
                <!-- <list_content :items="items"></list_content> -->
                  <div class="content">
                    <ul>
                      <li><a href="javascript:;" class="title" @click="anchor('about')">关于我</a></li>
                      <li><a href="javascript:;" class="title" @click="anchor('contact')">联系我</a></li>
                      <li><a href="javascript:;" class="title" @click="anchor('us')">关于本站</a></li>
                      <li><a href="javascript:;" class="title" @click="anchor('friend')">友情链接</a></li>
                    </ul>
                  </div>
              </div>
            </el-col>
        </el-row>
      </div>
  </div>
</template>

<script>
import { anchor } from "../../static/js/public.js";

const arr = [
  "富强",
  "民主",
  "文明",
  "和谐",
  "自由",
  "平等",
  "公正",
  "法治",
  "爱国",
  "敬业",
  "诚信",
  "友善"
];
const setStyle = (obj, json) => {
  for (var i in json) {
    obj.style[i] = json[i];
  }
};

let index = 0;

export default {
  mixins: [anchor],
  data() {
    return {
      // items:[]
    };
  },
  components: {},
  created() {
    // this.$http.get('/api/goods').then((data)=>{
    //   this.items=data.body.data;
    // })
  },
  methods: {
    btn_link(){
      alert('别点了 主页还没写呢，手点烂了都点不开')
    },
    clickTips: function(e) {
      if (index >= arr.length) {
        index = 0;
      }
      let newA = document.createElement("a");
      newA.className = "click_tips";
      let styles = {
        left: `${e.pageX}px`,
        top: `${e.pageY - 20}px`
      };
      newA.innerHTML = arr[index];
      setStyle(newA, styles);
      document.getElementById("page").appendChild(newA);
      index++;
      newA.addEventListener("animationend", () => {
        document.getElementById("page").removeChild(newA);
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.main {
  background: #f8f8fd;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.4), 0 0 30px rgba(10, 10, 0, 0.1) inset;
  margin: 0 10px;
  padding: 10px;
  > .title {
    font-size: 18px;
    padding: 5px 0;
  }
  .card {
    border-top: 1px solid #eee;
    .card-title {
      margin: 20px 0 10px;
      font-size: 26px;
    }
    .txt {
      font-size: 16px;
      margin: 0 20px 10px;
    }
    > ul {
      padding: 20px 30px;
      > li {
        padding: 10px 0;
      }
    }
    a {
      color: #4d6dad;
      &:hover {
        color: #223253;
        background-color: #f4efeb;
      }
    }
    .update {
      padding: 20px;
      h3 {
        margin: 0;
      }
      > p {
        margin: 10px;
      }
      > ul {
        padding: 0 30px;
      }
    }
    .row-link {
      padding: 20px;
      .link {
        margin: 5px;
        &:hover {
          color: #0085a1;
        }
      }
    }
  }
}
.aside {
  background: #f8f8fd;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.4), 0 0 30px rgba(10, 10, 0, 0.1) inset;
  > .title {
    font-size: 16px;
    font-weight: 600;
    border-bottom: 1px solid #ddd;
    padding: 10px 15px;
  }
  .content {
    padding: 15px 30px;
    li {
      list-style-type: none;
      padding: 5px 16px;
      position: relative;
      &::before {
        content: "";
        width: 6px;
        height: 6px;
        background: #333;
        position: absolute;
        left: 0;
        top: 13px;
        border-radius: 50%;
      }
      > a {
        color: #4d6dad;
        &:hover {
          color: #223253;
        }
      }
    }
  }
}

@media (min-width: 768px) {
  //pc
  .main {
    margin: 0 20px;
    padding: 20px;
    > .title {
      font-size: 30px;
    }
  }
}
</style>
<style>
/* click_tips */
.click_tips {
  color: red;
  position: absolute;
  transition: all 0.3s;
  animation: click_translateTop 1s;
}

@keyframes click_translateTop {
  0%,
  100% {
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  100% {
    transform: translateY(-30px);
  }
}
</style>

