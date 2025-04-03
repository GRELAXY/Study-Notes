# vscode的git使用

1. 下载git和注册github
2. 绑定git的user_name和email（vscod中授权登录就行了）
3. publish brunch的时候网络不行开始建立代理

````python
git config --global http.proxy socks5://127.0.0.1:7890
git config --global https.proxy socks5://127.0.0.1:7890
````

*这是我ikuuu的代理端口*



`git log`可查看当前目录下提交修改记录
