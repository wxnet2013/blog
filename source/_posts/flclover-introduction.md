---
title: 开源Web框架Flclover
date: 2017-08-23 23:10:01
tags: [草稿,node,koa,flclover,async]
---
## 设计初衷
TODO Node 中间层

## 设计原则
企业级Web框架

## Show me the code

* app/router.js

```javascript
module.exports = (router, controller) => {
  router.get('/', controller.home.index);
};
```

* app/controller/home.js

```javascript
exports.index = async (ctx) => {
  ctx.body = 'Hello, Flclover!';
};
```

## 架构图
![flclover](http://7xocsy.com1.z0.glb.clouddn.com/blog/flclover.png)

## 常用中间件
### 代理中间件 flclover-proxy
```javascript
const dt = await ctx.proxy({
   data: { source: data() },
   data1: { source: data1(), cache: 5 },
   data2: { source: data2(), cache: 10 },
   data3: { source: data3(), cache: 15 },
});
```

### 定时任务中间件 flclover-schedule
```javascript
module.exports = (app) => {
  return {
    schedule: {
      interval: '1s',
      immediate: true,
    },
    async task(service) {
      // do something
    },
  };
};
```
## 相关链接
1. [意见反馈](https://github.com/TalkingData/flclover/issues)
2. [中间件列表](https://github.com/search?q=topic%3Aflclover-middleware&type=Repositories)
