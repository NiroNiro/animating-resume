<template>
  <div id="app">
    <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
    <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
  </div>
</template>

<script>
  import StyleEditor from './components/StyleEditor'
  import ResumeEditor from './components/ResumeEditor'
  import './assets/reset.css'

  export default {
    name: 'app',
    components: {
      StyleEditor,
      ResumeEditor
    },
    data() {
      return {
        interval: 30,
        currentStyle: '',
        enableHtml: false,
        fullStyle: [
          `/*
* 你好，我叫熊锐
* 作为一名前端工程师，这是我的求职简历
*/

/* 首先给所有元素加上过渡效果 */
* {
  -webkit-transition: all .3s;
  transition: all .3s;
}
/* 白色背景太单调了，我们来点背景 */
html {
  color: rgb(222,222,222); background: rgb(0,43,54);
}
/* 文字离边框太近了 */
.styleEditor {
  padding: .5em;
  border: 1px solid;
  margin: .5em;
  overflow: auto;
  width: 45vw; height: 90vh;
}
/* 代码高亮 */
.token.selector{ color: rgb(133,153,0); }
.token.property{ color: rgb(187,137,0); }
.token.punctuation{ color: yellow; }
.token.function{ color: rgb(42,161,152); }

/* 加点 3D 效果呗 */
html{
  -webkit-perspective: 1000px;
          perspective: 1000px;
}
.styleEditor {
  position: fixed; left: 0; top: 0;
  -webkit-transition: none;
  transition: none;
  -webkit-transform: rotateY(10deg) translateZ(-100px) ;
          transform: rotateY(10deg) translateZ(-100px) ;
}

/* 接下来我给自己准备一个编辑器 */
.resumeEditor{
  position: fixed; right: 0; top: 0;
  padding: .5em;  margin: .5em;
  width: 48vw; height: 90vh;
  border: 1px solid;
  background: white; color: #222;
  overflow: auto;
}
/* 好了，我开始写简历了 */


`,
          `
/* 这个简历好像差点什么
 * 对了，这是 Markdown 格式的，我需要变成对 HR 更友好的格式
 * 简单，用开源工具翻译成 HTML 就行了
 */
`
          ,
          `
/* 再对 HTML 加点样式 */
.resumeEditor{
  padding: 2em;
}
.resumeEditor h2{
  display: inline-block;
  border-bottom: 1px solid;
  margin: 1em 0 .5em;
}
.resumeEditor ul,.resumeEditor ol{
  list-style: none;
}
.resumeEditor ul> li::before{
  content: '•';
  margin-right: .5em;
}
.resumeEditor ol {
  counter-reset: section;
}
.resumeEditor ol li::before {
  counter-increment: section;
  content: counters(section, ".") " ";
  margin-right: .5em;
}
.resumeEditor blockquote {
  margin: 1em;
  padding: .5em;
  background: #ddd;
}
`],
        currentMarkdown: '',
        fullMarkdown: `熊锐
----

web前端开发工程师

* TEL: 17683713133
* e-mail: xrwithyuan@gmail.com

技能
----

* 熟练使用 JavaScript、HTML5、CSS3。
* 熟练使用 JQuery、Zepto JS库。
* 熟练使用 angularJS、Vue.js主流框架。
* 熟练使用 BootStrap、Ionic、WeUI、AmazeUI框架开发各式响应式网站。
* 熟练使用 SASS 等 CSS 预处理器。
* 掌握 webpack + vue + vuex + vue-router + vue-resource + zepto + swiper + weui 开发
* 掌握 git、svn 版本控制工具，可以通过版本控制工具进行代码管理。
* 了解 Node.js，能用 Node.js 搭建服务器和写简单的后端。
* 了解 php 和 MySql数据库，可以做基本的php后台搭建以及数据库的增删改查，会写简单的API接口
* 对Objective-C有一定了解, 并且有自己单独做过的上线项目
* 了解Java和C



工作经历
----

> #### 2014/11 – 2017/3


> #### 杭州煜泰网络科技有限公司  |  web前端开发工程师


> ##### 行业内别：外包  |  企业性质：合资


> ##### 工作描述：
        1. 参与公司各个项目的前端开发工作，根据设计图进行响应式开发布局；
        2. 运用 Vue.js、Angular.js 进行移动页面的开发，能使用 rem 布局，
            完成页面开发制作及维护工作；
        3. 运用 HTML + CSS + JavaScript + jQuery / Zepto 技术对所参与的项目进行开发和维护，
            完成相关页面的改版需求，协调测试人员及跟进开发过程中的 bug；
        4. 与后台开发人员进行相关的沟通，并完成前后台的对接工作；
        5. 负责手机 APP 页面的设计；


项目经历
----

### 爱牙库商城移动端(已上线)

> #### 项目描述：
        一款牙科材料移动端商城(http://m.51aiyaku.com/)
> #### 应用技术：
        1. 使用Angular.js 框架构建单页面应用；
        2. 使用Ionic 框架搭建项目。
        3. 使用Lazyload 技术优化前端性能。
        4. 使用 jQuery 实现必要的节点操作进行交互。
        5. 模拟JSON数据通过自己用php编写的php后台来模拟API传输数据进行项目调试。

> #### 责任描述：
        1. 负责一级路由’home’(首页)、’mainCategory’(分类)以及
            二级路由’ product/info’(商品详情)的HTML构建以及逻辑交互。
        2. 负责配合后台完成 Ajax 请求、数据渲染等。


### 亿好金服(http://www.ehaojf.com/)

> #### 项目描述：
        一款互联网投资理财金融服务平台
> #### 应用技术：
        1. 使用 HTML、CSS 完成页面的静态布局，处理浏览器兼容性问题。
        2. 用 Javascript、jQuery 实现页面交互效果。
        3. 使用 css sprite 优化图片、加快图片加载速度。
        4. 使用sass 进行css样式的预处理。
        5. 使用gulp 进行代码合并压缩并且实现自动化构建。
        6. 模拟JSON数据通过自己用php编写的php后台来模拟API传输数据进行项目调试。
> #### 责任描述：
        1. 负责公司核心频道的 web 前端的开发工作。
        2. 使用 HTML5+CSS3 实现 PC 端网页的排版制作。
        3. 负责活动页的动画效果的制作。
        4. 负责配合后台完成 Ajax 请求、数据渲染等。


### 爱途旅游webApp

> #### 项目描述：
        一款旅游游记的分享平台
> #### 应用技术：
        1. 使用angularJS框架构建单页面应用，三层路由嵌套，
            通过MVVM设计模式双向数据绑定实现数据驱动页面。
        2. 使用weUI和swiper部分组件。
        3. 使用gulp进行代码压缩合并并且做自动化构建。
        4. 使用自定义过滤器、自定义指令、服务和控制器处理不同情况的数据，
            通过组件和路由实现组件化和模块化。
        5. 使用sass进行css样式预处理。



** 感谢浏览我的简历，谢谢 **



`
      }
    },
    created() {
      this.makeResume()
    },

    methods: {
      makeResume: async function () {
        await this.progressivelyShowStyle(0);
        await this.progressivelyShowResume();
        await this.progressivelyShowStyle(1);
        await this.showHtml();
        await this.progressivelyShowStyle(2)
      },
      showHtml: function () {
        return new Promise((resolve, reject) => {
          this.enableHtml = true;
          resolve();
        })
      },
      progressivelyShowStyle(n) {
        return new Promise((resolve, reject) => {
          // 获取设置的延时时长
          let interval = this.interval;

          let showStyle = (async function () {
            // 获取第this.fullStyle数组的第n个元素
            let style = this.fullStyle[n];
            // 空判断,如果style为空,则跳出函数
            if (!style) {
              return
            }
            // 计算前 n 个 style 的字符总数
            let length = this.fullStyle.filter((_, index) => index <= n).map((item) => item.length).reduce((p, c) => p + c, 0);
            let prefixLength = length - style.length;
            // 判断已打印的字符长度是否小于字符串总长度
            if (this.currentStyle.length < length) {
              let l = this.currentStyle.length - prefixLength;
              // 截取一个字符
              let char = style.substring(l, l + 1) || ' ';
              // 拼接到已展示的字符串中
              this.currentStyle += char;
              // 如果上一个字符是换行符,则执行
              if (style.substring(l - 1, l) === '\n' && this.$refs.styleEditor) {
                this.$nextTick(() => {
                  this.$refs.styleEditor.goBottom();
                })
              }
              // 设置延时器,递归,延时下次调用
              setTimeout(showStyle, interval);
            } else {
              resolve();
            }
          }).bind(this);
          showStyle();
        })
      },
      progressivelyShowResume() {
        return new Promise((resolve, reject) => {
          let length = this.fullMarkdown.length;
          let interval = this.interval;
          let showResume = () => {
            if (this.currentMarkdown.length < length) {
              this.currentMarkdown = this.fullMarkdown.substring(0, this.currentMarkdown.length + 1);
              let lastChar = this.currentMarkdown[this.currentMarkdown.length - 1];
              let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2];
              console.log(prevChar);
              if (prevChar === '\n' && this.$refs.resumeEditor) {
                this.$nextTick(() => this.$refs.resumeEditor.goBottom())
              }
              setTimeout(showResume, interval);
            } else {
              resolve();
            }
          };
          showResume();
        })
      }
    }
  }

</script>

<style scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  html {
    min-height: 100vh;
  }

  * {
    -webkit-transition: all .3s;
    transition: all .3s;
  }
</style>
