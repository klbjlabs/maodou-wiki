### 服务端定时任务

安装
```
meteor add percolate:synced-cron
```

server/tasks.js

``` js
SyncedCron.add({
  name: 'Crunch some important numbers for the marketing department',
  schedule: function(parser) {
    // parser is a later.parse object
    return parser.text('every 2 hours');
  },
  job: function() {
    var numbersCrunched = CrushSomeNumbers();
    return numbersCrunched;
  }
});

SyncedCron.start();
```
> 可以add多个任务。
> 使用[later.js](http://bunkat.github.io/later/)语法



---
参考资料：
* [https://atmospherejs.com/percolate/synced-cron](https://atmospherejs.com/percolate/synced-cron)
* [http://bunkat.github.io/later/](http://bunkat.github.io/later/)
* [https://themeteorchef.com/recipes/santa-spotter/](https://themeteorchef.com/recipes/santa-spotter/)