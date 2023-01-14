# vue-homework（2023-1-14）

2022年寒假学习Vue3并尝试做的小项目

## 主要内容

- Element Plus组件库的使用
- 基本的Vue3语法和数据渲染操作
- 学习简单的分页操作
- 学习简单的数据过滤操作

## 未理解的知识点

- 组件传值
- ref，computed等函数的作用
- 未涉及网络数据请求
- 。。。

## 将Vue3项目部署到GitHub上

- 本文讲如何将Vue项目的dist文件夹部署到Github Page上，目的是可以在线访问前端效果，这样不需要自己购买服务器，当然任何静态文件夹都可以这样做，不止局限于Vue
- 操作步骤如下：
1、首先在Git上建立一个项目，如vue-echarts-map
2、然后将本地项目push到远程master （非必须）

```sh
echo "# vue-echarts-map" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/dongkelun/vue-echarts-map.git
git push -u origin master
```

3、主要是下面这一步，将打包后的dist文件夹push到gh-pages

```sh
npm run build
git checkout -b gh-pages
git add -f dist
git commit -m 'first commit'
git subtree push --prefix dist origin gh-pages
```

4、将仓库分支切换到gh-pages然后save就可以了

> 备注：
1、我这里做了域名绑定 dongkelun.github.io=>gh.dongkelun.com 没有域名的直接访问`http://dongkelun.github.io/vue-echarts-map`
2、还有首先你先创建一个类似yourgithubname.github.io这样格式的GitHub仓库，然后按上面把dist文件夹（即静态文件夹）push到gh-pages分支，就会自动部署了。域名绑定只需在dongkelun.github.io仓库做一次即可，即加一个CNAME，然后域名加解析，这里不做详细说明~
3、如果你不用gh-pages分支，或者你不想分享源代码，你可以直接将dist文件夹push到master分支，但是需要自己在Setting里设置，用哪个分支部署，默认是gh-pages分支,如echarts-map
