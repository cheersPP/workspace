## 实验环境 ： Ubuntu、CentOS

# 使用 RVM 安装 Ruby

RVM 能在系统中安装和管理多个 Ruby 版本。同时还能管理不同的 gem 集。支持 OS X、Linux 和其它类 UNIX 操作系统。

- 安装 RVM

		$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
		$ curl -sSL https://get.rvm.io | bash -s stable

- 载入 RVM 环境

		$ source ~/.rvm/scripts/rvm

- 检查一下是否安装正确

		$ rvm -v


- 用 RVM 安装 Ruby 环境

		$ rvm install 2.3.1

  - 使用centos安装ruby，需要先用yum安装一系列包

			$ yum install -y autoconf automake bison gcc-c++ libffi-devel libtool readline-devel sqlite-devel zlib-devel libyaml-devel openssl-devel


- 安装bundler

		$ rvm gemset list
		$ sudo gem install bundler

  - [簡介 Bundler](https://www.cnblogs.com/yulongzhou/p/6392329.html?utm_source=itdadao&utm_medium=referral)

# 安装rails

	$gem install rails


## ubuntu 搭建过程中遇到的问题
- sudo apt-get update

		E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
		E: Sub-process returned an error code
解决方法：

		$ sudo pkill -KILL appstreamcli
		$ wget -P /tmp https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_amd64.deb

-  bundle install

			Gem::Ext::BuildError: ERROR: Failed to build gem native extension.
			......
			An error occurred while installing nokogiri (1.8.1), and Bundler cannot
			continue.
			Make sure that `gem install nokogiri -v '1.8.1'` succeeds before bundling.
 原因是缺少依赖包，nokogiri安装出错
  解决方法：

			$ sudo apt-get install ruby-dev

## CentOS 搭建过程中遇到的问题

 - RVM安装ruby后，ruby -v 提示 ruby:未找到命令
解决方法：

		$ echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"' >>~/.bashrc
		$ source ~/.bashrc
		$ ruby -v
