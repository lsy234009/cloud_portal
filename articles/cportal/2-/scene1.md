## 如何快速更换导航栏

### 整体增加一个皮肤

如下面所示增加一个青色皮肤来改变整体导航栏色系

第一步：在potal数据库中增加一行记录，如下图增加的“青色”的记录

![](/articles/cportal/2-/images/1-1.png)
<p align="center">图 1</p>

其中id对应于步骤的css文件名，如增加的青色皮肤id为test对应test.css

第二步：添加portal\themes\css\test.css，test.css具体格式如下

	.cloud {
	    background:#F0FFF0;
	}
	
	.navbar-portal .navbar-toggle .icon-bar {
	    background-color: #ffffff;
	}
	
	.navbar-portal .navbar-toggle:hover, .navbar-portal .navbar-toggle:focus {
	    color: #fff;
	    background-color: #F0FFF0;
	}
	
	.navbar-toggle-button.collapse.in {
	    background: #F0FFF0;
	}
	
	.navbar-portal .navbar-nav li a i {
	    color: #fff;
	}
	
	#username span {
	    color: #000;
	}
	
	.site-menubar {
	    background: #F0FFF0;
	}
	
	.menubar > li.active {
	    background: #f4f4f4;
	    border-left: 2px solid #f4f4f4;
	    border-top: 1px solid #f4f4f4;
	    border-bottom: 1px solid #f4f4f4;
	    padding: 7px 0;
	}
	
	.menubar li i, .icon-name, .menubar li.active .wb-chevron-right-mini {
	    color: #757575;
	}
	
	.menubar-hover {
	    background: #f4f4f4;
	}
	
	.menubar li.active i, .menubar li.active .icon-name, .menubar li.active .wb-chevron-right-mini {
	    color: #424242;
	}
	
	.menubar li.menubar-hover i, .menubar-hover .icon-name, .menubar li.menubar-hover .wb-chevron-right-mini {
	    color: #424242;
	}
	
	.menubar-menu {
	    background: #f4f4f4;
	}
	
	.menubar-menu a:hover {
	    background: #d3d3d3;
	}
	
	.menubar-menu a {
	    color: #757575;
	}
	
	.menubar-hover a {
	    color: #424242;
	}
	
	.site-menubar.sidebar-left.collapse {
	    box-shadow: 5px 0 5px 0 rgba(117,117,117,0.4);
	}
	
	.site-menubar.sidebar-left.collapse.in{
	    box-shadow: 0 0 0 0;
	}
	
	.navbar-portal .navbar-nav li a {
	    color: #333333;
	}
	
	.navbar-portal .navbar-nav li a i {
	    color: #757575;
	}

第三步：添加portal\logo_test.png和skin_test.png图片，它们分别对应添加皮肤的导航栏的logo和选择皮肤里面的“青色”上面的缩略图

实例效果图如下

![](/articles/cportal/2-/images/1-2.png)

![](/articles/cportal/2-/images/1-3.png)