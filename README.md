<h1><a href="#" title="yep-ui 官网"></h1>


yecui 是基于公司内部项目构建的一个跨屏前端框架和前端规范。`现阶段移动优先`
	
框架-简单地说，就是一些事先写好的css，你只需要给你的html元素加上一些特定的类，就可以快速的得到一些想要的效果。

## 项目开发
- 大中型项目,页面开发套PHP壳,公共页面维护方便
- 基本结构
```
	项目名称/
	├── src/
	|	├── assets/
	|	|	├── css/
	|	|	|	├── base.css		//css reset + function 通用解决方案
	|	|	|	├── yeps.css		//yecui 组件文件
	|	|	|	└── solution.css	//基于各产品个性解决方案
	|	|	├── img/
	|	|	|	├── ...			//基础ui图片
	|	|	|	├── fonts/		//字体文件
	|	|	|	├── design/		//设计源文件
	|	|	|	└── project/		//项目专有图片
	|	|	├── js/
	|	|	|	├── app/			//各页面具体js
	|	|	|	├── lib/			//js框架
	|	|	|	└── common/		//通用js
	|	|	└── less/
	|	|		├── view/			//less编译文件
	|	|		└── widget/		//yecui 组件库
	|	├── mock/
	|	├── page/
	|	|	├── layout/			//公共模块
	|	|	├── tmpl/				//模板文件
	|	|	├── view/				//主体页面
	|	|	└── widget/			//页面组件
	└── tool/
```
## 模块组织规范

yecui 的样式模块组织方式追求扁平化的方式，分为三个层级：
- 基础框架（reset +  function + iconfont + 栅格）
- 通用模块（符合 yeps 规范的样式模块）
- 页面样式（继承通用模块,开发人员进一步开发）

##关于命名空间

建议使用 - 来做命名空间上的区隔，最小化两个模块之间的命名冲突。
#####这种模块化的命名方式会很好地避免样式之间的冲突，特别推荐在团队中使用。参见 [网易前端框架NEC-分类方法](http://nec.netease.com/standard/css-sort.html)
1. 重置`reset`和默认`base``tags`：消除默认样式和浏览器差异，并设置部分标签的初始样式，以减少后面的重复劳动！你可以根据你的网站需求设置！
2. 统一处理：建议在这个位置统一调用背景图（这里指多个布局或模块或元件共用的图）和清除浮动（这里指通用性较高的布局、模块、元件内的清除）等统一设置处理的样式！
3. 布局 `grid` `.g-`：将页面分割为几个大块，通常有头部、主体、主栏、侧栏、尾部等！
4. 模块 `module` `.m-`：通常是一个语义化的可以重复使用的较大的整体！比如导航、登录、注册、各种列表、评论、搜索等！
5. 元件 `unit` `.u-`：通常是一个不可再分的较为小巧的个体，通常被重复用于各种模块中！比如按钮、输入框、loading、图标等！
6. 功能 `function` `.f-`：为方便一些常用样式的使用，我们将这些使用率较高的样式剥离出来，按需使用，通常这些选择器具有固定样式表现，比如清除浮动等！不可滥用！
7. 皮肤 `skin` `.s-`：如果你需要把皮肤型的样式抽离出来，通常为文字色、背景色（图）、边框色等，非换肤型网站通常只提取文字色！非换肤型网站不可滥用此类！
8. 状态 `.z-`：为状态类样式加入前缀，统一标识，方便识别，她只能组合使用或作为后代出现（.u-ipt.z-dis{}，.m-list li.z-sel{}），具体详见命名规则的扩展相关项。
- `ui模块` 
```css
	/*常用系统组件 包括 */
	.ui-navbar{} 	 			/* 导航条 */
	.ui-header{} 	 			/* 页眉 */
	.ui-footer{} 	 			/* 页脚 */
	.ui-titbar{} 	 			/* 标题栏 */
	.ui-menu{} 	 				/* 菜单 */
	.ui-button{} 	 			/* 按钮 */
	.ui-tabs{} 					/* tab切换 */
	.ui-forms{} 				/* 表单 */
	.ui-alert{} 				/* 提示信息 */
	.ui-dropdown{} 				/* 下拉框 */
	.ui-slider{} 				/* 滑动内容 */
	.ui-select{} 				/* 选择器 */
	.ui-share{} 				/* 分享 */
	.ui-breadcrumb{} 			/* 面包屑 */
	.ui-close{} 				/* 关闭 */
	.ui-icon{} 					/* 图标 */
	.ui-list{} 					/* 列表 */
	.ui-pages{} 				/* 分页 */
	.ui-step{} 					/* 步进条 */
	.ui-table{} 				/* 表格 */
```
- `fn模块` 
```css
	.fn-clear{} 				/* 清除浮动 */
	.fn-hide{} 					/* 隐藏元素 */
	.fn-left{} 					/* 左浮动 */
	.fn-right{} 				/* 右浮动 */
	.fn-omit{} 					/* 单行移除省略 */
	.fn-clamp{} 				/* 多行移除省略 */
	.fn-rmb{} 					/* 金钱样式 */
	.fn-linear{} 				/* 简单渐变 */

	/*功能类的组件 包括 */
	.fn-variables{} 			/* less变量 */
	.fn-utility{} 				/* 公用 */
	.fn-grid{} 					/* 布局 */
	.fn-animation{} 			/* 动画 */
	.fn-mixins{} 				/* 混合函数 */
```


## CSS书写规范 

参考 [google的html、css代码规范](http://www.cnblogs.com/2050/archive/2012/04/26/2470947.html)

1.多人开发,推荐竖版写法,方便修改维护
```css
	.yp-title {
		position: relative;
		top: 100px;
		left: 100px;
		font-weight: bold;
	}
```
2.统一采用” - “对class中的字母分隔
```css
	.yp-title {
		font-weight: bold;
	}
```
3.在紧跟属性名的冒号后,和属性名和{之间 使用一个空格
```css
	.hotel-content {
    	font-weight: bold;
	}
```
4.多选择器规则之间（必须）换行
```css
	a.btn,
	input.btn,
	input[type="button"] {
	     ......
	}
```
5.如果css属性的值为0,则后面不要带上单位。除非真的是需要。
```css
	.obj {
	    left: 0;    
	}
```
6.推荐使用css书写顺序,按照这样的顺序书写可见提升浏览器渲染dom的性能
```css
	.hotel-content {
	     /* 定位 */
	     display: block;
	     position: absolute;
	     left: 0;
	     top: 0;
	     /* 盒模型 */
	     width: 50px;
	     height: 50px;
	     margin: 10px;
	     border: 1px solid black;
	     / *其他* /
	     color: #efefef;
	}
```
7.小图片（必须）sprite 合并

8.IE Hack List
```css
	selector {
	     property: value;     /* 所有浏览器 */ 
	     property: value\9;   /* 所有IE浏览器 */ 
	     property: value\0;   /* IE8 */
	     +property: value;    /* IE7 */
	     _property: value;    /* IE6 */
	     *property: value;    /* IE6-7 */
	}
```
9.避免不必要的 CSS 选择符嵌套,选择符嵌套在必要的情况下一般不超过三层；选择符叠加一般不多于两个。
```css
	/* 不推荐 */
	.ui.form.input .fields.error .field .ui.selection.dropdown .menu .item:hover {
	    ...
	}
```
10.ID和class的命名尽可能短，并符合语义。
```css
	/* 不推荐 */
	.navigation {}
	.atr {}
	/* 推荐 */
	.nav {}
	.author {}
```









### 图标使用
- ui 彩色图标建议使用雪碧图合并一起,减小请求数
- 扁平化纯色图标尽量使用 font-face 代替 雪碧图,推荐使用> [淘宝图标库Iconfont](http://www.iconfont.cn/)

### 命名建议
常用状态有：hover, current, selected, disabled, focus, blur, checked, success, error 等
	
### 简写的建议
```
	title = tt	content = cnt
```
## 移动端开发说明
#### 单位的使用
rem是否能替代px 作为基础单位  
- 推荐阅读 [webapp rem的变革](http://isux.tencent.com/web-app-rem.html)
- 最好有一套快速切换px ,rem 为单位的解决方案
