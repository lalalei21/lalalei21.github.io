---
title: Hexo 主题 yilia 优化
date: 2019-04-12 11:53:19
tags: hexo
toc: true
comments: true
reward: true
---
好吧，我承认自己是一个外貌协会。
既然倒腾了这个博客，就尽量让自己感到舒服😌。
废话不多说了，开始吧。

## 1. 添加网站浏览量统计
- 不蒜子官网：http://busuanzi.ibruce.info/
- 安装脚本（必选），在 <code>themes\yilia\layout\_partial\footer.ejs</code> 最后添加：
``` html
<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
```
<!--more-->
- 添加网站访问量标签（可选），在 <code>footer.ejs</code> 插入如下代码：
``` html
<span id="busuanzi_container_site_pv">
  本站总访问量<span id="busuanzi_value_site_pv"></span>次
</span>
<span id="busuanzi_container_site_uv">
  本站访客数<span id="busuanzi_value_site_uv"></span>人次
</span>
```
- 添加文章点击量标签（可选），修改 <code>themes\yilia\layout\_partial\article.ejs</code> 的 <code>header</code> 标签：
```html
<header class="article-header">
  <%- partial('post/title', {class_name: 'article-title'}) %>
  <!--显示阅读次数-->
  <% if (!index && post.comments){ %>
    <br/>
    <a class="cloud-tie-join-count" href="javascript:void(0);" style="color:gray;font-size:14px;cursor: text">
    <span class="icon-sort"></span>
    <span id="busuanzi_container_page_pv" style="color:#f173ac;font-size:14px;">
      阅读数: <span id="busuanzi_value_page_pv"></span>次 &nbsp;&nbsp;
    </span>
    </a>
  <% } %>
  <% if (!post.noDate){ %>
  <%- partial('post/date', {class_name: 'archive-article-date', date_format: null}) %>
  <% } %>
</header>
```
&nbsp;
## 2. 添加网站评论
- gitalk 项目地址：https://github.com/gitalk/gitalk
- 创建 OAuths Apps：
1. Application name 和 Application description	填入自己喜欢的名称和描述
2. Homepage URL 和 Authorization callback URL 填入域名
3. 注册之后，会看到Client ID和Client Secret

- 在<code>_config.yml</code>文件中进行相关配置：
``` yaml
# 配置gitalk
gitalk: 
  enable: true
  client_id: 1c92f03bc20099211872
  client_secret: 5c5b458be40fd177ac8592700e296b1465d86f36
  repo: lalalei21.github.io
  owner: lalalei21
  admin: lalalei21
```

- 安装脚本文件和使用容器，在<code>_posts</code>文件夹中新建<code>gitalk.ejs</code>：
``` html
<!-- gitalk.ejs -->
<div id="gitalk-container" style="padding: 0 30px;"></div>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>

<script>
var gitalk = new Gitalk({
  clientID: '<%=theme.gitalk.client_id%>',
  clientSecret: '<%=theme.gitalk.client_secret%>',
  repo: '<%=theme.gitalk.repo%>',
  owner: '<%=theme.gitalk.owner%>',
  admin: '<%=theme.gitalk.admin%>',
  id: '<%=page.date%>',      // Ensure uniqueness and length less than 50
  distractionFreeMode: false  // Facebook-like distraction free mode
})

gitalk.render('gitalk-container')
</script>
```

- 在 <code>article.ejs</code> 的末尾添加：
``` html
<% if(theme.gitalk.enable){ %>
  <%- partial('post/gitalk', {
      key: post.slug,
      title: post.title,
      url: config.url+url_for(post.path)
    }) %>
<% } %>
```

&nbsp;
## 3. 添加看板娘
- 项目地址：https://github.com/EYHN/hexo-helper-live2d
- 安装模块
``` bash
npm install --save hexo-helper-live2d
```
- 向 hexo 的配置文件 <code>_config.yml</code> 加入代码：
``` yaml
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  log: false
  model:
    use: live2d-widget-model-miku
    scale: 1.2
  display:
    position: right
    width: 150
    height: 300
    hOffset: 18 # bottom
    vOffset: 30 # right
  mobile:
    show: true
  react:
    opacity: 0.7
```
- 安装模型
```yaml
npm install 模块名
# 同时修改配置文件
model:
  use: live2d-widget-model-miku
```
1. 更多现有模型请[点击](https://github.com/xiazeyu/live2d-widget-models)
2. 更多安装方案请查看[github项目](https://github.com/EYHN/hexo-helper-live2d/blob/master/README.zh-CN.md#b-%E7%9B%B8%E5%AF%B9%E4%BA%8E%E5%8D%9A%E5%AE%A2%E6%A0%B9%E7%9B%AE%E5%BD%95%E7%9A%84%E8%87%AA%E5%AE%9A%E4%B9%89%E8%B7%AF%E5%BE%84)

- 发现新大陆，请参考文章：
1. [给博客添加能动的看板娘 (Live2D)- 将其添加到网页上吧](https://imjad.cn/archives/lab/add-dynamic-poster-girl-with-live2d-to-your-blog-02)
2. [网页添加 Live2D 看板娘](https://www.fghrsh.net/post/123.html)
3. [Live2D Widget](https://github.com/stevenjoezhang/live2d-widget)


&nbsp;
更多优化持续更新...^^