# vuepress类Hexo的yilia主题

## 使用
1. <code>npm i vuepress-theme-similar-yilia</code>
2. 在 <code>.vuepress/config.js</code> 中提供一个 theme 选项：
```javascript
module.exports = {
  theme: 'vuepress-theme-similar-yilia'
}
```
3. 基本配置和[vuepress默认配置](https://www.vuepress.cn/default-theme-config/#%E4%B8%BB%E9%A1%B5-homepage)的差不多
4. [YAML front matter](https://jekyllrb.com/docs/frontmatter/)语法部分和hexo配置差不多
## 为什么
18年5月29我用hexo脚手架在github pages上搭建了一个博客,当默认的主题不是很好看,于是在网上搜罗一圈发现[yilia](git@github.com:litten/hexo-theme-yilia.git)主题挺好看的,于是就用起了这个主题。一段时间后,想修改主题,就按照作者的说明进行了修改,但是打包时出现了问题,原来webpack版本太低。我就直接在打包后的代码上做修改,但是很不方便。几天后,我把该主题的所有依赖都更新到最新,修改打包配置,调试通过后提交了dev分支到作者的git仓库,顺便看了一下代码提交情况,发现最近一次提交在17年11月15,而且打包问题已经有人提交了Pull requests,但没有合并。于是想用尤大的[vuepress](https://www.vuepress.cn/)实现这样一个主题。
## 说干就干
刚开始准备完全自己写,写着写着发现[vuepress](https://www.vuepress.cn/)的自定义主题真的是完完全全的自定义,Markdown的样式都没有,而且[vuepress](https://www.vuepress.cn/)默认主题的响应式做的非常好,于是决定这个基础上做了修改,就有了这个。
