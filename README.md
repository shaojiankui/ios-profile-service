# profile-service
iOS Profile Service, Based on Apple's Over-the-Air Profile Delivery and Configuration article.

https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/iPhoneOTAConfiguration/Introduction/Introduction.html

0.使用breww或者rvm安装ruby,macos自带ruby不好用.我安的是2.6.0.

1.bundler初始化项目
gem install bundler
or
sudo gem install bundler

bundle install --path vendor/bundle

2.https证书文件转换.


.key 转换成 .pem：

openssl rsa -in temp.key -out temp.pem
.crt 转换成 .pem：

openssl x509 -in tmp.crt -out tmp.pem