---
layout: post
title:  pod时遇到的错误（1） 
date:   2016-2-2 13:22:11
category: "iOS"
---



##下面的错误

	mac-deiMac:~ mac$ pod search
		/Library/Ruby/Site/2.0.0/rubygems/dependency.rb:296:in `to_specs': Could not find 	'cocoapods' (>= 0) among 13 total gem(s) (Gem::LoadError)
	from /Library/Ruby/Site/2.0.0/rubygems/dependency.rb:307:in `to_spec'
	from /Library/Ruby/Site/2.0.0/rubygems/core_ext/kernel_gem.rb:47:in `gem'
	from /usr/bin/pod:22:in `<main>'
	mac-deiMac:~ mac$ pod search sudo gem install cocoapods 
		/Library/Ruby/Site/2.0.0/rubygems/dependency.rb:296:in `to_specs': Could not find 'cocoapods' (>= 0) among 13 total gem(s) (Gem::LoadError)
	from /Library/Ruby/Site/2.0.0/rubygems/dependency.rb:307:in `to_spec'
	from /Library/Ruby/Site/2.0.0/rubygems/core_ext/kernel_gem.rb:47:in `gem'
	from /usr/bin/pod:22:in `<main>'


###解决方案：

1). sudo gem uninstall --all

2). sudo gem install cocoapods

3). pod setup

OK!完美解决！！