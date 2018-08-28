<template>
  <div id="app">
    <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
    <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
  </div>
</template>

<script>
  import StyleEditor from './components/StyleEditor'
  import ResumeEditor from './components/ResumeEditor'
  import ThankEditor from './components/ThankEditor'
  import './assets/reset.css'

  export default {
    name: 'app',
    components: {
      StyleEditor,
      ResumeEditor,
      ThankEditor
    },
    data() {
      return {
        interval: 10,
        currentStyle: '',
        enableHtml: false,
        fullStyle: [
          `/*
* Inspired by http://strml.net/
* 大家好，我是郭峰。
* 我来写一份简历！
*/

/* 首先给所有元素加上过渡效果 */
* {
  transition: all .1s;
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


`,`
/* 这个简历好像差点什么
 * 对了，这是 Markdown 格式的，我需要变成对 HR 更友好的格式
 * 简单，用开源工具翻译成 HTML 就行了
 */
`, `
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
`,`
/*
 * 特别鸣谢。
    */
    `, `
    /* 再对 HTML 加点样式 */
    .thankEditor{
      padding: 2em;
    }
    .thankEditor h2{
      display: inline-block;
      border-bottom: 1px solid;
      margin: 1em 0 .5em;
    }
    .thankEditor ul,.thankEditor ol{
      list-style: none;
    }
    .thankEditor ul> li::before{
      content: '•';
      margin-right: .5em;
    }
    .thankEditor ol {
      counter-reset: section;
    }
    .thankEditor ol li::before {
      counter-increment: section;
      content: counters(section, ".") " ";
      margin-right: .5em;
    }
    .thankEditor blockquote {
      margin: 1em;
      padding: .5em;
      background: #ddd;
    }
    `],
        currentMarkdown: '',
        fullMarkdown: [

          `郭峰

  

坐标：北京。


[下载离线简历](http://guofeng007.github.io/anires/static/resume.pdf)

---

# 联系方式  


- 姓名:郭峰
- 手机:17710672859   
- Email:tianfengjingjing@gmail.com 
- QQ/微信:616585129                  






    
---
# 个人信息
- 郭峰/男/1990
- 研究生/中南民族大学/计算机应用技术
- 工作年限：3年
- 期望职位：Android高级程序员，应用架构师
- 期望薪资：面议
- 期望城市：北京
- GitHub：   [guofeng007](https://github.com/guofeng007) 、技术博客：[Blog](https://guofeng007.github.io/) 、CSDN：   [csdn](http://blog.csdn.net/rajesh0)



---

# 工作经历-百度 ( 2015年7月 ~ 2018年至今 ）

**百度金融-支付业务部-Android端：负责人**

**百度金融-支付业务部-TC晋升委员会：评委**
## 百度钱包插件框架

- 参与百度钱包插件化项目。通过插件化，不同的业务可以独立开发、集成、更新。作为主要参与者，完成插件框架整体设计，主要核心实现。通过插件化项目，对安卓系统底层运行机制更加熟练，为后续持续创新奠定坚实的基础。目前该项目已经进入众测阶段，插件平台也在建设中。支付SDK已经通过插件化方式下发，后续会扩展三方业务接入，为APP提供更多的功能。

## 百度钱包Hybrid框架 
- 完成百度钱包Hybrid混合开发框架，支持webview+jsBridge+原生控件+离线等特性。作为框架主要负责人，不但完成了Hybrid的特性，更增加了原生控件的支持，使得H5的体验逼近原生应用。同时在弱网和无网环境下首屏展示时间缩短扫100ms以内，支持离线浏览。后期增量更新也大大减少了APP的网络流量消耗，极大的提升了用户体验。该框架上线之后，为FSG金融业务提供了强有力的容器支持，能够满足移动互联网时代快速迭代的需求。现已接入消费信贷、理财、医美O2O等30+业务，成为百度金融业务开发的核心框架。

## 百度金融风控SDK
- 负责网络基础框架，主要职责：设计网络库，通过HttpDNS IP直连，心跳保活等技术优化网络性能。
- 负责OCR图像识别，活体识别，以及风控能力输出。

## 百度钱包人脸支付
- 负责百度钱包人脸支付相关技术架构，一期基于 Pad版本人脸支付，适用于中小支付场景。二期基于 RGB+深度3D 摄像头+开发板方案，在识别速度，准确率，安全性上有了很大的提升，适用于任何场景。

## 百度钱包支付SDK 
- 参与百度钱包SDK相关功能开发，独立完成扫一扫、Crash统计、SchemePay、分散认证等模块。作为独立功能负责人，从需求、系统设计开始，持续跟进后期上线、迭代、维护等整个生命周期。通过对各模块的开发，积累了作为TopicLeader所需的各项业务知识。各项功能不断扩展百端钱包的线下使用场景，截止2016年底，百度钱包绑卡强账户数目已经破亿。
- 参与支付流程优化改造、一卡通充值优化以及对外接入等工作。通过与其他团队以及部门的合作，提升了自己的跨团队沟通能力，有效保障各项业务合作顺利进行。整个优化改造项目在上线后，取得良好的用户评价，绑卡成功率提升5%、支付成功率提升2%。 
- 专注移动端优化，能够使用LeakCanary分析内存泄漏，追踪ANR，提高APP运行性能。提升代码质量，通过CodeReview，FindBugs, Lint等工具优化代码质量。通过对SDK的持续优化，使得对外输出接入包的size、质量能够和竞品支付宝、微信对齐，现已接入百度旗下20多款产品，同时外部公司也在不断接入。

## 新技术研究   

###热修复
- 对微信Tinker、QZone超级补丁、AndFix、美团Robust等热修复框架源码有一定的了解。

---
#获得奖项

- 2015 百度MSG移动服务事业群最佳新人奖 
- 2016 百度FSG金融事业部技术达人奖
- 2017 百度FSG磐石最佳团队奖

---
<br>
#实习经历
- 2015 阿里巴巴共享业务事业部、百度钱包、CVTE

---
#教育经历（成绩5%）
- 2012.09 - 2015.06 中南民族大学/计算机应用技术/硕士研究生 
- 2008.09 - 2012.06 中南民族大学/计算机科学与技术/本科 

---
## 技能清单
- 源码调试经验丰富，熟练使用各种 Android 调试工具和方法，可以应付各种复杂问题，有较好的好问题分析和解决能力。
- 独立编译Android系统源码、对Android OS系统体系结构有一定的理解。
- 熟悉 tcp/udp/http/https 协议，设计通用网络协议。
- 掌握framework跨进程通信Binder、四大组件、Handler原理以及常见的系统问题。
- 深入了解常见的Android开源框架、对高性能程序设计、架构有较多的工程经验。
- 对Hybrid、插件化、热修复等新技术有一定的研究。对开源项目兴趣浓厚

---
## 参考技能关键字
- android framework
- 插件化、热修复、Hybrid、webview
- ReactNative、EventBus/HermesEventBus
- ndk/jni、svn/git/github

---
## 致谢
感谢您花时间阅读我的简历，期待能有机会和您共事。

离线简历
----

[下载简历](http://www.sitexa.org/anires/static/resume.pdf)

`,`
鸣谢
----


`]
      }
    },
    created() {
      this.makeResume()
    },

    methods: {
      makeResume: async function () {
        await this.progressivelyShowStyle(0)
        await this.progressivelyShowResume()
        await this.progressivelyShowStyle(1)
        await this.showResumeHtml()
        await this.progressivelyShowStyle(2)
        await this.progressivelyShowStyle(3)
        await this.progressivelyShowThanks()
      },
      showResumeHtml: function () {
        return new Promise((resolve, reject) => {
          this.enableHtml = true
          resolve()
        })
      },
      progressivelyShowStyle(n) {
        return new Promise((resolve, reject) => {
          let interval = this.interval
          let showStyle = (async function () {
            let style = this.fullStyle[n]
            if (!style) {
              return
            }
            // 计算前 n 个 style 的字符总数
            let length = this.fullStyle.filter((_, index) => index <= n).map((item) => item.length).reduce((p, c) => p + c, 0)
            let prefixLength = length - style.length
            if (this.currentStyle.length < length) {
              let l = this.currentStyle.length - prefixLength
              let char = style.substring(l, l + 1) || ' '
              this.currentStyle += char
              if (style.substring(l - 1, l) === '\n' && this.$refs.styleEditor) {
                this.$nextTick(() => {
                  this.$refs.styleEditor.goBottom()
                })
              }
              setTimeout(showStyle, interval)
            } else {
              resolve()
            }
          }).bind(this)
          showStyle()
        })
      },
      progressivelyShowResume() {
        return new Promise((resolve, reject) => {
          let resume = this.fullMarkdown[0]
          let length = resume.length
          let interval = this.interval
          let showResume = () => {
            if (this.currentMarkdown.length < length) {
              this.currentMarkdown = resume.substring(0, this.currentMarkdown.length + 1)
              let lastChar = this.currentMarkdown[this.currentMarkdown.length - 1]
              let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2]
              if (prevChar === '\n' && this.$refs.resumeEditor) {
                this.$nextTick(() => this.$refs.resumeEditor.goBottom())
              }
              setTimeout(showResume, interval)
            } else {
              resolve()
            }
          }
          showResume()
        })
      },
      progressivelyShowThanks() {
        return new Promise((resolve, reject) => {
          this.enableHtml = true
          let thanks = this.fullMarkdown[1]
          let length = thanks.length
          let interval = this.interval
          let showThanks = () => {
            if (this.currentMarkdown.length < length) {
              this.currentMarkdown = thanks.substring(0, this.currentMarkdown.length + 1)
              let lastChar = this.currentMarkdown[this.currentMarkdown.length - 1]
              let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2]
              if (prevChar === '\n' && this.$refs.thankEditor) {
                this.$nextTick(() => this.$refs.thankEditor.goBottom())
              }
              setTimeout(showThanks, interval)
            } else {
              resolve()
            }
          }
          showThanks()
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
    box-sizing: border-box;
    }
</style>
