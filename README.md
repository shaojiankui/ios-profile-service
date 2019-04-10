# profile-service
iOS Profile Service, Based on Apple's Over-the-Air Profile Delivery and Configuration article.

https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/iPhoneOTAConfiguration/Introduction/Introduction.html

# 配置:
### 0.使用breww或者rvm安装ruby,macos自带ruby不好用.我安的是2.6.0.  2.4.0 Gemfile中不用解开openssl注释,因为2.6.0.  2.4.0中自带openssl模块

### 1.bundler初始化项目
gem install bundler
or
sudo gem install bundler

bundle install --path vendor/bundle

####  plist库有问题,所以我手动改了下.
 `require': /Users/jakey/Desktop/ios-profile-service/plist/lib/plist/binary.rb:161: invalid multibyte escape: /[\x80-\xff]/

### 2.https证书文件转换.


.key 转换成 .pem：

openssl rsa -in temp.key -out temp.pem
.crt 转换成 .pem：

openssl x509 -in tmp.crt -out tmp.pem

# 运行:
### 进入到项目根目录(所有的证书都是脚本自动生成的自签名证书) 线上环境用非自签名的证书即可.
ruby profile-service.rb

提示  [2019-04-10 10:53:59] INFO  WEBrick::HTTPServer#start: pid=41905 port=8443 运行成功.

手机访问https://ip:8443 即可

点击ca安装下自签名的根证书.

点击enroll 用户名密码 apple apple

如果换了请求ip，要删除ssl证书（ssl_private.pem，ssl_cert.pem）。重新运行脚本。脚本里的根据ip编号自动替换证书逻辑有点问题。

# Bundle命令详解：

### 显示所有的依赖包

bundle show

### 显示指定gem包的安装位置

bundle show [gemname]

### 安装依赖包到项目根目录(在项目目录执行)

bundle install --path vendor/bundle

