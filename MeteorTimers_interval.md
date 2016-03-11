# 计时器 Interval 方法
---

```js
var func = function() {
  console.log("foobar");
}
var delay = 500;       // ms
var task = Meteor.setInterval(func, delay);

Meteor.clearInterval(task);    // 使用创建时返回的id来终止任务
```