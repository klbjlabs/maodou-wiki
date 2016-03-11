# 制作 Meteor Package
---

#### 1.申请开发者账号
  [atmospherejs.com](https://atmospherejs.com/)
>  在制作 meteor 自定义包之前，你首先要注册一个 atmospherejs 的账号，这个账号与 meteor 官方账号是通用的。这样你才能把你的包发布到网络上，自己或者他人才能使用 meteor add 方式添加你的包到项目中。

#### 2. 登陆在atomspherejs 账号

>  注册完 atmospherejs 的账号后，你需要在终端下登陆你的账号，这样创建包时程序才知道你提交的包归属与哪个作者。

  ``` bash
  $ meteor login     
  Username: klbjlabs
  Password:                                     
  Logged in as klbjlabs. Thinks...
  ```



#### 创建包结构
``` bash
meteor create --package klbjlabs:test       # 用户名:包名
```


#### 包发布到 ATMOSPHERE
``` bash
meteor publish --create	# 第一次发布时使用
meteor publish             # 之后每次更新版本可以直接发布
```

#### 隐藏包
```
/＊ 该包会被标记小红旗在下一个版本发布后取消标记＊／
meteor admin set-unmigrated klbjlabs:test
```

#### 升级包
```
meteor update --packages-only
```

#### 包结构
```js
package.js

/* 包信息的设定 */
Package.describe({
  name: 'klbjlabs:test',            // 包的名字
  version: '0.0.1',                 // 版本号
  summary: ‘Just test’,             // 
  git: 'https://github.com/klbjlabs/klbjlabs-test',  // 对应的 github 地址
  documentation: 'README.md'                         // 可以将 README 显示在atomsphere上
});

/* 包的依赖环境 */
Package.onUse(function(api) {
  api.versionsFrom('1.2.1');			// 包所支持Meteor的最低版本
  api.use('ecmascript');			    // 依赖包
  api.use('iron:router@1.0.12', ["server", "client"]);	// 带版本的依赖包格式

  api.use(['minimongo', 'mongo-livedata', 'templating'], 'client');	// mongo and template

  // ls -l | awk '{print "api.addFiles(\""$9"\", \"client\");"}'
  api.addFiles('client/routes.js', 'client');			   // 添加文件
  api.addFiles("client/posts/post_edit.html", "client");	// Client
  api.addFiles("lib/collections.js");				       // Both
  api.addFiles("server/publications.js", "server");		 // Server

  api.export('Posts');	// 数据库
});
```
##### 相关资料:
* [**Discover Meteor**](http://zh.discovermeteor.com/chapters/creating-a-meteor-package/)
* [**The Meteor Chef**: Writing a Package](https://themeteorchef.com/recipes/writing-a-package/)
* [**邓佳的笔记**](https://github.com/nmgwddj/meteor-notes/blob/master/02_meteor%20Package%20%E5%88%B6%E4%BD%9C.md)