#项目目录及文件名
##项目目录
1、components 业务无关的组件，第三方开源或自己开发。目前已有的组件（添加到首屏幕、tab组件、gmu套件、mustache模版引擎、iscroll、播放器）
2、lib 项目框架（zepto、zepto插件、underscore） 
3、main  项目的入口文件
4、modules 业务模块，其中一个文件是一个独立的模块。
5、views  展现层，每个文件对应一个模块相关的展现层。
6、tips 展现层用到的html代码。

##文件命名
1、所有文件名用小写。
2、入口文件和模块文件用后缀标明项目（_iphone、_android）

##SVN外部链接的文件及目录
1、components／player  目录，播放器独立开发
2、lib  H5项目共享，目前两个项目引用（webapp、webapp_passport）
3、modules／pvstats.js

##目录注解
├── components    和业务无关的目录，用于放一些通用的组件。
│   │   ├── add2home.js
│   │   ├── bootstrap-tab.js
│   │   ├── gmu                         百度的GMU组件目录
│   │   │   ├── touch.js
│   │   │   ├── zepto.extend.js
│   │   │   ├── zepto.imglazyload.js    图片懒加载组件
│   │   │   └── zepto.ui.js
│   │   ├── hogan.js
│   │   ├── iscroll.js
│   │   └── player                        播放器路基，采用svn的外部链接引入项目里
│   ├── lib      项目框架目录
│   │   ├── class.js
│   │   ├── events.js
│   │   ├── index.js   框架的入口文件，提供给base.js，新增的框架模块请修改这个入口文件。
│   │   ├── jquery.proxy.js  jquery的api代理到zepto下面，提供给统计代码使用，保证统计代码和主站的一致。
│   │   ├── jsdeferred.js
│   │   ├── jsdeferred.zepto.js
│   │   ├── namespace.js
│   │   ├── underscore.js
│   │   ├── zepto.cookie.js
│   │   ├── zepto.data.js
│   │   └── zepto.js
│   ├── main   同主站，项目的入口文件。其中文件名以_android、_iphone结尾的文件针对不同的设备，无后缀的文件，是不区分设备的。
│   │   ├── about.js
│   │   ├── base.js
│   │   ├── channel_list.js
│   │   ├── ent_play.js
│   │   ├── ent_play_android.js  android only，文件代码复用了公共设备的代码，如ent_play.js
│   │   ├── feedback.js
│   │   ├── friend.js
│   │   ├── home.js
│   │   ├── home_iphone.js     iphone only
│   │   ├── mv_play.js
│   │   ├── mv_play_android.js
│   │   ├── player.js
│   │   ├── qa.js
│   │   ├── search.js
│   │   ├── search_empty.js
│   │   ├── search_result.js
│   │   ├── sitemap.js
│   │   ├── sys_error.js
│   │   ├── tv_play.js
│   │   ├── tv_play_android.js
│   │   ├── va_play.js
│   │   └── va_play_android.js
│   ├── modules        业务模块目录
│   │   ├── album_pager.js
│   │   ├── bottom_menu.js
│   │   ├── channel.js
│   │   ├── channel_tips.js
│   │   ├── entalbum.js
│   │   ├── feedback.js
│   │   ├── hide_location_iphone.js
│   │   ├── home.js
│   │   ├── loadmore.js
│   │   ├── mvalbum.js
│   │   ├── ort_player.js
│   │   ├── play.js
│   │   ├── player.js
│   │   ├── pvstats.js
│   │   ├── related_list.js
│   │   ├── search.js
│   │   ├── search_result.js
│   │   ├── sitemap.js
│   │   ├── smartbanner.js
│   │   ├── sys_error.js
│   │   ├── tvalbum.js
│   │   ├── unicom.js
│   │   └── vaalbum.js
│   ├── tpls       业务模块的html代码模版
│   │   ├── home_popup.js
│   │   ├── mvalbum.js
│   │   ├── tvalbum.js
│   │   ├── unicom.js
│   │   └── vaalbum.js
│   └── views      业务模块的view层（接收module层的数据，并render页面）
│       ├── mvalbum.js
│       ├── tvalbum.js
│       ├── unicom.js
│       ├── vaalbum.js
│       └── view.js