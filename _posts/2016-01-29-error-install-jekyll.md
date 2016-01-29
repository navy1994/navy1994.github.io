---
layout: post
title: 安装Jekyll博客的问题
date: 2016-01-29 13:45:12
category: "Jekyll博客"
---

##错误
    ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
    mac-deiMac:~ mac$ sudo ARCHFLAGS=-Wno-error=unused-command-line-argument-hard- error-in-future gem install jekyll
    Password:
	Building native extensions.  This could take a while...
	ERROR:  Error installing jekyll:
	ERROR: Failed to build gem native extension.

    /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby extconf.rb
	checking for ffi.h... *** extconf.rb failed ***
	Could not create Makefile due to some reason, probably lack of necessary
	libraries and/or headers.  Check the mkmf.log file for more details.  You may
	need configuration options.

	Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include
	--without-opt-include=${opt-dir}/include
	--with-opt-lib
	--without-opt-lib=${opt-dir}/lib
	--with-make-prog
	--without-make-prog
	--srcdir=.
	--curdir
	--ruby=/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby
	--with-ffi_c-dir
	--without-ffi_c-



##解决方法

####安装ruby
rvm install 2.1.1

####使用ruby-2.1.1
rvm use ruby-2.1.1

####安装Jekyll
sudo ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future gem install jekyll