---
title: 关于Hexo配置的一些小帮助
date: 2022-11-07 21:34:53
tags:
---
想来你们也应该会跟我一样遇到一些小小的问题。

接下来，我将讲述如何解决这些问题。

附录：[Hexo配置文件](/norender/config.hexo.yml)*提示：本文件正在翻译中*

- 使用Github Pages部署时，CNAME（自定义域名标识符）文件总是被覆盖？
	解决方法：
	```yml
	# 配置文件directory部分
	skip_render:
		- CNAME
	# 将skip_render参数添加CNAME
	```
	注意：将CNAME文件写入source/内，每次编译都会自动复制。
		如果您使用我的教程，仓库完整路径应该为：“<main>(branch)/docs/source/”

- 想要美观的URL固定链接？
	解决方法：
	```yml
	# 配置文件URL部分
	# 参考：https://hexo.io/zh-cn/docs/permalinks#%E5%8F%98%E9%87%8F
	# ps：Frontmatter指的是文章开头被三个"-"圈起来的部分，格式为YAML(YML)
	# 分别更改这两个属性：
	permalink: :category/:name.html # 推荐，格式为：http(s)://<你的域名>/<文章所属分类>/<文件名>.html，美观大方且简洁！
	pretty_urls:
		trailing_index: true # 是否显示"/index.html"
		trailing_html: true # 是否显示".html"
	```
