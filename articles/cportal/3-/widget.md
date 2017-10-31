## 云门户 Widget开发

### 什么是Widget

Widget,是一小块可以在任意一个基于HTML的Web页面上执行的代码，它的表现形式可能是视频，地图，新闻，小游戏等等。它的根本思想来源于代码复用，通常情况下，Widget的代码形式包含了DHTML,JavaScript以及Adobe Flash。

![](/articles/cportal/3-/images/w-1.PNG)
<p align="center">图 1</p>

Portal中widget，遵循OpenSocial 2.5.1的规范

![](/articles/cportal/3-/images/w-2.PNG)
<p align="center">图 2</p>

#### Widget-与Portlet区别

Portlet  服务器端渲染；形式单一；重量级

Widget   客户端渲染；注册形式多样；轻量

![](/articles/cportal/3-/images/w-3.PNG)
<p align="center">图 3</p>

#### Widget-实例

简洁版

![](/articles/cportal/3-/images/w-4.PNG)
<p align="center">图 4</p>

经典版

![](/articles/cportal/3-/images/w-5.PNG)
<p align="center">图 5</p>

### Widget分类

#### 标准widget

Iframe Widget

Inline Widget

#### 扩展widget

片段

URL

Js插件

### Widget通信

widget和server通信，采用AJAX技术

格式如下

	$.ajax({
			type:'get',   
	 		dataType:'json',  
			contentType: 'application/json',
	   		url:'/meheco/nbbidata/getsimulatedata',
	  		success:function(res) {    
				  …
			} , 
			error:function(XMLHttpRequest){
				…  		
			 }
	});

Gadget 之间的事件机制也就是通常所说的发布/订阅事件是基于 OpenAjax Hub 2.0 规范实现的。

Shindig 中 Gadget 之间的通信通过 pubsub 实现，展现 Gadget 的页面相当于主应用，页面上的 Gadget 为各个客户应用。如果某页面需要支持声明了 pubsub2 的 Gadget，就需要在页面加载时加载 OpenAjax Hub 相关的 JavaScript 文件，并且创建 Managed Hub。Shindig 中的 pubsub2 特性针对 Gadget 容器和 Gadget 两个上下文分别定义了不同的 JavaScript 文件。

#### pubsub-2 特性定义
	
	<feature> 
	    <name>pubsub-2</name> 
	    <dependency>globals</dependency> 
	    <dependency>org.openajax.hub-2.0.5</dependency> 
	    <gadget> 
	        <script src="pubsub-2.js"/> 
	        <script src="taming.js"/> 
	    </gadget> 
	    <container> 
	        <script src="pubsub-2-router.js"/> 
	    </container> 
	</feature>
	
### Widget属性

#### 模块属性- ModulePrefs

概要属性

描述widget标题、id、描述、配置ui等

#### 用户属性

显示属性

描述在widget加载时需要用的配置信息

#### 示例

待办任务集成widget

![](/articles/cportal/3-/images/w-6.PNG)
<p align="center">图 6</p>

#### 数据类型

字符串（string）

枚举（enum）

集合（list）

布尔（bool）

隐藏（hidden）

#### Widget属性-数据类型-示例

字符串（string）

	<UserPref name="height" display_name="高度" datatype="string" default_value="360" />

枚举（enum）

	<UserPref name="produc" display_name="产品" datatype="enum">
	      <EnumValue value="nc65" display_value="nc65" />
	      <EnumValue value="nc63" display_value="nc63" />
	</UserPref>

集合（list）

	<UserPref name="system" display_name="系统" datatype="list" default_value="NC5|NC6" />

布尔（bool）

	<UserPref name="isenable" display_name="启用" datatype="bool" default_value="t" />

隐藏（hidden)

	<UserPref name="mode" display_name="模式" datatype="hidden" default_value="1" />

![](/articles/cportal/3-/images/w-7.PNG)
<p align="center">图 7</p>

#### Widget属性示例

![](/articles/cportal/3-/images/w-8.PNG)
<p align="center">图 8</p>

### 开发widget

Widget 开发人员需要熟悉js、react、uui、comonjs等主流前端开发技术，编写代码时要遵循AMD等大众规范，具体代码编写参考Google JavaScript 编码规范指南：<http://alloyteam.github.io/JX/doc/specification/google-javascript.xml>

一个widget xml定义结构
	
	<?xml version="1.0" encoding="UTF-8"?>
	<Module><ModulePrefs title="待办-任务"></ModulePrefs>
	<Content type="html">
	<![CDATA[
	          Css引入  
	          Js引入
	          Js编写
	          Css编写
	          Html编写
	         系统变量
	]]>
	</Content>
	</Module>

#### 开发widget-css导入

代码示例

	require('css!./indexlink.css'); 
	require('css!../../font/mehecofont/iconfont.css');

通过require加载好处：加载一次，减少网络流量


#### 开发widget-Js 引入

代码示例

	require(["/portal/widget/CommonLink6/linkTask.js"],function(task){
	    var hei = getWidgetAttr(‘height’);
	    task.init(hei);
	});

#### 开发widget-Js编写

代码示例-Js编写

	define(function(require, exports, module ){
	    var styles = require('css!./indexvision.css');
	    var icon = require('css!../../font/mehecofont/iconfont.css');
	    var viewModel={
	        pageInit:function(){
	
	        }
	    };
	    return {
	        init: function(){
	            viewModel.pageInit();
	        }
	    }
	});

#### Css编写

  模板：

	.框架class  widget皮肤class  业务class{
	     ….
	}

  示例：

	.commonlink .u-panel-heading{
	    background: #eeeeef;
	    border-radius: 10px;
	    height: 40px;
	    line-height: 40px;
	} 

  说明：

	1：框架class会在页面主题切换时联动
    2：widget 皮肤class 会在布局个性化时编辑小部件皮肤时跟随联动
    3：业务class，具体widget业务含义

#### Html编写

Html编写要遵循uui 控件要求，html数据绑定、事件、

示例：

	<html>
	    <head>
	        <title></title>
	    </head>
	    <body>
	        <div class="oa-task width-full oaApprove">
	            <div class="u-panel">
	                <div class="u-panel-heading clearfix">
	                    <span class="pull-left"><strong>OA待办审批</strong></span>
	                    <ul class="pull-right height-full OAsc">
	                        <li class="pull-left title">
	                            <a href="javaScript:void(0)" searchtype="unread" data-bind="click:$root.search">待办审批</a>
	                        </li>
	                        <li class="pull-left title">
	                            <a href="javaScript:void(0)" searchtype="incoming" data-bind="click:$root.search">收文审批</a>
	                        </li>
	                    </ul>
	                </div>
	                <div class="u-panel-body">
	                    <div u-meta='{"id":"oaGrid","data":"dataTable","type":"grid","onBeforeClickFun":"onClickFun"}'>
	                        <div options='{"field":"title","dataType":"String","editType":"string","sortable":true,"canSwap":true}'></div>
	                        <div options='{"field":"sender","dataType":"String","editType":"string" ,"renderType":"timeRender","sortable":true}'></div>
	                        <div options='{"field":"senddate","dataType":"String","editType":"string","sumCol":true}'></div>
	                    </div>
	                </div>
	            </div>
	        </div>
	    </body>
	</html>


#### 系统变量

在开发widget过程中，会涉及到系统级变量的获取，如：context(/portal、/integration)、widgetid等。
系统目前提供如下系统变量的注入：

(1).${context}，应用上下文
使用示例如下：

![](/articles/cportal/3-/images/1.PNG)
<p align="center">图 9</p>
 
(2).${widgetId}, 小部件标识
使用示例如下：

![](/articles/cportal/3-/images/2.PNG)
<p align="center">图 10</p>





