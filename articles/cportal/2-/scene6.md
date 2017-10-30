## 如何配置widget属性

### widget属性基础知识

概述

Widget属性分为模块属性和用户属性，模块属性是概要属性，描述widget标题、id、描述、配置ui等。用户属性是显示属性，是在widget加载时需要用的配置信息。
模块属性对应widget定义xml中的ModulePrefs 用户属性对应widget 定义xml中的UserPref

Widget规范里定义的属性示例如下：

	<?xml version="1.0" encoding="UTF-8"?>
	<Module>
	<ModulePrefs title="待办-任务"
	description="MyTask"
	userpref_url="/integration/pages/approve/approve.html?w=500&amp;h=500">
	</ModulePrefs>
	<UserPref status="1" name="height" display_name="高度" datatype="string" default_value="360"/> 
	<UserPref status="1" name="count" display_name="条数" datatype="string" default_value="6"/>
	<UserPref status="0" name="system" display_name="系统" datatype="list" default_value="NC5|NC6"/> 
	<UserPref name="produc" display_name="产品" datatype="enum">
	        <EnumValue value="nc65" display_value="nc65" />
	        <EnumValue value="nc63" display_value="nc63" />
	</UserPref>
	<Content type="html">
	  <![CDATA[
		...

1、属性数据类型

Widget属性分为种5种：隐藏（hidden）、布尔（bool）、集合（list）、枚举（enum）、字符串（string）

它们各自使用方式如下：

(1) 字符串（string）
	`<UserPref name="height" display_name="高度" datatype="string" default_value="360" />`

(2) 枚举（enum）
  
	`<UserPref name="produc" display_name="产品" datatype="enum">
	      <EnumValue value="nc65" display_value="nc65" />
	      <EnumValue value="nc63" display_value="nc63" />
	</UserPref>`


(3) 集合（list）
	`<UserPref name="system" display_name="系统" datatype="list" default_value="NC5|NC6" />`

(4) 布尔（bool）
	`<UserPref name="isenable" display_name="启用" datatype="bool" default_value="t" />`

(5) 隐藏（hidden）
	`<UserPref name="mode" display_name="模式" datatype="hidden" default_value="1" />`

2、属性状态
Widget 属性状态分为：管理级和用户级

status="1"  ：管理员和普通用户可见
status="0" : 管理员可见

3、属性默认值
Widget属性默认值，以xml里定义为准，如：default_value="360"，用户、管理员配置的属性在运行时会覆盖该属性。

4、属性配置UI
Widget属性配置UI指在设计器页面编辑某个widget时的界面，当widget开发人员指定特定界面时，portal将直接打开它。
如下：

	<?xml version="1.0" encoding="UTF-8"?>
	<Module>
	<ModulePrefs title="待办-任务"
	description="MyTask"
	userpref_url="/integration/pages/approve/approve.html?w=500&amp;h=500">

不指定时，portal提供默认简单的属性配置界面，如下图：

![](/articles/cportal/2-/images/6-1.png)

默认界面控件解析说明：

![](/articles/cportal/2-/images/6-2.PNG)

