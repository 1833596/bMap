bMap 是一个通过 apicloud 中bMap模块实现的一个简单的地图。

本项目是我为了研究这个模块写的一点实例仅做参考，如果你有好的想法或用法欢迎你向我提出。
 
注意：实际项目中在不同的页面我们通常使用 execScript 或者缓存等来进行页面间的传值，为了公用一些数据。但 bMap 中某些方法者不然，这也是我在使用这个模块的时候发现的这个问题。如：我模仿百度地图 ‘到这去’ 来搜索需要的路线方案时，我使用 searchRoute 这个方法在 routePlanList.html 中执行，然后再选中路线以后再在首页地图上画出路线，结果没有任何反应。后来向平台技术咨询才知，百度提供的这个sdk会存在一个虚拟路线的情况，简单的说就是先画好路线但不显示。在执行 searchRoute 的时候它除了实际返回了路线方案，实际还在已打开的地图上画了虚拟的路线（这个时候你看不见路线，调用 drawRoute 后就才显示），而这种数据不能用execScript来传递。所以如果你遇到这样的问题你要把所有以 open 为前提的方法都封装到那个你打开地图的页面，其他的页面通过 execScript 配合使用来实现逻辑。

如果你将此代码运行到你的项目中首先你必须：
将这个项目中 `config.xml`  删掉，并在你的项目 `config.xml` 中配置你的 bMap 
