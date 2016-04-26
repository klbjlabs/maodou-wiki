# 当使用pages分页时的count
> 当使用 `alethes:pages` 包来做分页，以及瀑布流的时候。有时需要显示服务器上数据的总条数，但是此时数据是根据用户浏览来分步加载的，会造成count显示不正确的情况

这里可以使用 `tmeasday:publish-counts` 包来解决
```
meteor add tmeasday:publish-counts
```

### Server
```
Meteor.publish('publication', function() {
   Counts.publish(this, 'numberOfPosts', Posts.find());
   Counts.publish(this, 'numberOfUsers', Users.find());
});
```

### Client
```
Meteor.subscribe('publication')
```
获取count
```
Counts.get('numberOfUsers')
```

相关资料