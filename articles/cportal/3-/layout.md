## 布局模板扩展


### 配置数据库，扩展布局模板

pt_layout_template表里面增加一行记录即增加一个布局模板

实例一：
例如下面增加的布局column8-4（一行两列）
其中tpl确定布局样式：

	<div class="row">
		<div class="col-md-8 ui-grid" id="widgetbox1">
		</div>
		<div class="col-md-4 ui-grid" id="widgetbox2">
			col-md-4
		</div>
	</div>

![](/articles/cportal/3-/images/p-1.PNG)
<p align="center">图 1</p>

注意：其中column需满足各分列值加起来一共是12

效果图如下：

![](/articles/cportal/3-/images/p-2.PNG)
<p align="center">图 2</p>

实例二：
例如下面增加的row2-column4-column2（二行四列二列布局模板）
其中tpl确定布局样式：

	<div class="row">
		<div>
			<div class="col-md-3 ui-grid" id="widgetbox1">
			</div>
			<div class="col-md-3 ui-grid" id="widgetbox2">
			</div>
			<div class="col-md-3 ui-grid" id="widgetbox3">
			</div>
			<div class="col-md-3 ui-grid" id="widgetbox4">
			</div>
		</div>
		<div>
			<div class="col-md-6 ui-grid" id="widgetbox5">
			</div>
			<div class="col-md-6 ui-grid" id="widgetbox6">
			</div>
		</div>
	</div>

效果图如下：


![](/articles/cportal/3-/images/p-3.PNG)
<p align="center">图 3</p>