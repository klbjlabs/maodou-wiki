# Meteor Package 制作

Meteor Package 制作




申请开发者账号
http://meteor.com

创建包结构
meteor create --package jiatian:test

包发布到 ATMOSPHERE
meteor publish --create	// 第一次发布时使用
meteor publish			// 之后每次执行这个即可

隐藏包
/＊ 该包会被标记小红旗在下一个版本发布后取消标记＊／
meteor admin set-unmigrated klbjlabs:test


升级包
meteor update --packages-only

package.js

/* 包信息的设定 */
Package.describe({
  name: 'klbjlabs:test',
  version: '0.0.1',
  summary: ‘Just test’,
  git: 'https://github.com/klbjlabs/klbjlabs-test',
  documentation: 'README.md'
});

/* 包信息的设定 */
Package.onUse(function(api) {
  api.versionsFrom('1.2.1');			// 包所支持Meteor的最低版本
  api.use('ecmascript');			// 依赖包
  api.use('iron:router@1.0.12', ["server", "client"]);	// 带版本的依赖包格式

  api.use(['minimongo', 'mongo-livedata', 'templating'], 'client');	// mongo and template

  // ls -l | awk '{print "api.addFiles(\""$9"\", \"client\");"}'
  api.addFiles('client/routes.js', 'client');			// 添加文件
  api.addFiles("client/posts/post_edit.html", "client");	// Client
  api.addFiles("lib/collections.js");				// Both
  api.addFiles("server/publications.js", "server");		// Server

  api.export('Posts');	// 数据库
});

#####参考文献:
[http://zh.discovermeteor.com/chapters/creating-a-meteor-package/](http://zh.discovermeteor.com/chapters/creating-a-meteor-package/)
