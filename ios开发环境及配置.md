# iOS开发环境及工具

## XCode简介
xib-->Storyboard

UI的创建：

* 代码编写：纯代码创建UI
* Xib：UI能用xib就尽量用xib，iOS开发之xib技巧介绍：<http://www.ifun.cc/blog/2014/02/22/ioskai-fa-zhi-xibji-qiao-jie-shao/>
* Storyboard：能用storyboard就用storyboard, 一个storyboard里最好别装太多的UIViewController，这在结队开发中将不利，结队开发之多storyboard<http://www.ifun.cc/blog/2014/02/23/jie-dui-kai-fa-zhi-duo-storyboard/>

Autolayout-->SizeClass

* Autolayout：自适应布局，使用Auto Layout的坑<http://www.ifun.cc/blog/2014/07/23/shi-yong-auto-layoutde-keng/>
* SizeClass：iOS8新特性，是对老式UI思路的全新抽象：把各个设备屏幕（iphone4, 5, 6, iPad, Apple Watch?）以及它们的屏幕旋转状态都抽象成屏幕 Size 的变化<http://blog.sunnyxx.com/2014/09/09/ios8-size-classes/>

OC-->Swift

## Xcode常用插件

* Alcatraz

	在过去安装Xcode的插件非常麻烦，但是自从有了Alcatraz之后，这件事情就变的非常简单，不得不说Alcatraz是一个重要的里程碑，现在的版本是1.0，它完美支持Xcode5，如果你还没有使用过Alcatraz，我建议你先了解一下它
* XcodeColors

	XcodeColors是由Robbie Hanson开发的关于代码色彩的插件，这个插件配合CocoaLumberjack使用效果非常好，CocoaLumberjack是Robbie写的日至库，这个组合让我在这几年的编码中省了不少事
* XToDo

	这个插件不仅强调了TODO，FIXME,???和!!!注释，还为你提供了一个查看列表
* Backlight

	有些插件看上去微不足道但是他们却非常有用。Backlight就是这样的插件，它只是把当前正在编辑的行突出显示
* CocoaPods

	CocoaPods主要功能是为IOS和OS的开发进行依赖管理，如果你没有使用过它，我建议你一定要试一试。
CocoaPods plugin是CocoaPods在Xcode上的插件，它可以让你更容易地使用CocoaPods。它为CocoaPods添加了一个菜单项，如果你不喜欢用命令行，你可以使用这个插件

* ACCodeSnippetRepository

	使用它和你的Git库同步，如果你想手动导入一个Snippet需要很麻烦的步骤，通过这个插件你只需要点击几下鼠标

* GitDiff

	一个有图形界面的Git插件可以为开发者省去不少麻烦，虽然Tower 和SourceTree也都很不错，但是GitDiff能在Xcode中实时告诉我们现在的工程和上一个版本有哪些区别，这个功能是其他软件做不到的
	
* KSImageNamed

	虽然有些人说自动补全会让开发人员变懒，但它的确大大提高了开发效率，尤其是在写Object-C的时候，你甚至可以通过它补全一个图片命名

* Peckham

	添加引用文件有时候非常麻烦，如果你需要引入一个pod头文件，Xcode自带的自动补全自然帮不了你，这时候你可以用Peckham插件解决这个问题。Command+Control+P解决所有的引入
	
* FuzzyAutocomplete

	说到自动完成，大部分的iOS和OS X开发人员都依赖Xcode的自动完成功能。然而,Xcode的自动完成实现并不是完美的,你并不总能通过它得到你期望的建议或希望。它利用模式匹配算法来解决问题
	
## CocoaPods


CocoaPods安装和使用教程<http://code4app.com/article/cocoapods-install-usage>

Ruby安装流程(Mac版本)：

*  下载安装包：<https://www.ruby-lang.org/zh_cn/downloads/>
*  解压安装包

		$ tar -xvzf ruby-1.6.7.tgz
		$ cd ruby-1.6.7
* 配置并编译源代码：

		$ ./configure
		$ make
		
* 安装Ruby解释器：

		$ su -l root # 使用root用户
		$ make install
		$ exit       # 切换回普通用户
* 安装成功验证：

		$ruby -v
		ruby 2.3.1p112 (2016-04-26 revision 54768) [x86_64-darwin15]








	
