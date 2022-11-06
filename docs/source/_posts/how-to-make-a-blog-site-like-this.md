---
title: 如何做一个跟本站一样的博客？
date: 2022-11-06 10:50:50
tags:
---
# 概况
本站使用 Hexo(主体程序) + Next(主题) + Github Pages(托管)

# 依赖
1. Chocolatey

# 安装
1. Windows徽标键+R，打开运行框。输入powershell
2. 在powershell中输入
  ```bat
  choco install nodejs
  ```
  即可安装nodejs
3. 在powershell中输入
  ```bat
  choco install git
  ```
  即可安装git
4. 注册/登录你的Github账户，并创建一个仓库。复制克隆url备用。
5. 在一处右键，选择Git Bash打开。输入
  ```sh
  git clone <克隆url> <文件夹> // 文件夹随便取一个名字就行
  //等待完成
  cd <文件夹>
  npm install -g hexo-cli
  //等待完成
  hexo init docs
  //等待完成
  cd docs
  npm init
  //等待完成
  git clone https://github.com/theme-next/hexo-theme-next themes/next
  //等待完成
  ```
6. 参考[官方文档](https://hexo.io/zh-cn/docs/configuration)完成配置：
  输入
  ```sh
  vim _config.yml
  ```
  打开配置文件
  注：vim按i键进入编辑模式，编辑完成后按<ESC>键退出，再依次按下ZZ（大写，即按着shift）保存并退出 或 依次按下ZQ不保存并退出
7. 完成主题配置：
  输入
  ```sh
  vim themes/next/_config.yml
  ```
  参考翻译：[此处](/norender/config.theme.next.yml)
8. 安装git提交器：
  ```sh
  npm install hexo-deployer-git --save
  ```
9. 完善配置：
  ```sh
  vim _config.yml
  ```
  示例配置：
  ```Yml
  # 把最后的Deployment部分改为：
  deploy:
    type: git
    repo: <克隆url>
  ```
10. 完善脚本：
  ```sh
  vim package.json
  ```
  示例配置：
  ```json
  //把scripts部分修改为这样：
  "scripts": {
    "build": "hexo clean && hexo generate",
    "deploy": "hexo deploy",
    "server": "hexo server",
    "push": "hexo clean && git add -A && git commit -m \"some updates\" && git push origin main"
  },
  ```
11. 初始化提交：
  ```sh
  git --config user.name "<你的github用户名>"
  git --config user.email "<你绑定的邮箱>"
  git add -A
  //等待完成
  git commit -m "first commit"
  //等待完成
  git push -u origin main
  //可能会弹出登录窗口，登录即可。如果提示需要token，github头像->Settings->Developer settings->personal access token->add token
  //由于github经常抽风，在此步骤建议开启魔法。
  ```

# 使用
- 创建新文章
  ```sh
  hexo new <post(文章)/page(页面)/draft(草稿)/模板> <文件名>
  ```
  当运行结束后会给出文件地址，需要在该文件书写。
- 发布草稿
  ```sh
  hexo publish <post(文章)/page(页面)> <草稿名>
  ```
- 生成静态文件
  ```sh
  npm run build
  ```
  通常在提交/测试前运行此命令
- 提交静态文件
  ```sh
  npm run deploy
  ```
- 运行临时测试服务器
  ```sh
  npm run server
  ```
- 提交源码
  ```sh
  npm run push
  ```
  方便移动写作，一般在提交静态文件后运行

# 后记
翻译工作仍在继续中……

更多文件翻译：
- [Hexo配置文件](/norender/config.hexo.yml)
