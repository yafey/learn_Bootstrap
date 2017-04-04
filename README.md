
# 0x00. 什么是 Bootstrap
![](./ReadMe.image/what_is_boostrap.png)



# 0x01. Bootstrap 资源 

- [源码] https://github.com/twbs
- [英文原版教程] http://getbootstrap.com
- 【推荐】[中文教程] http://www.bootcss.com
	- a. 下载（生产版） ： 当前版本 v3.3.7
	- b. 基于jQuery
	- c. 引入


下面就是一个最简单的 Bootstrap 页面:
http://v3.bootcss.com/getting-started/#template

```
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge"> <!-- 该命令的含义是 如果是 IE 浏览器，使用最新的 edge 方式解析，提高渲染性能、显示效果等。-->
    <meta name="viewport" content="width=device-width, initial-scale=1">  <!-- 针对 移动端 的配置 -->
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap init Template</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">

	<!-- 针对 IE8 的支持  -->
    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://cdn.bootcss.com/html5shiv/3.7.3/html5shiv.min.js"></script>
      <script src="https://cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>你好，世界！</h1>

    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <!-- <script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script> -->
    <script src="js/jquery-1.11.1.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
  </body>
</html>
```

[{1.firstTemplate.html}@GitHub](https://github.com/yafey/learn_Bootstrap/blob/init&template/1.firstTemplate.html)


# 0x02. bootstrap 栅格系统 ： 前端布局 ， 页面分成 12 个网格

## 容器的概念 ： 通过不同 class 属性 区分。

###  分成 12 列
- row
- column


### 阈值（结合 container 容器 有各自的 默认值），来做响应式布局。
- `[0  ,768)`  : 手机的分辨率  ： auto 自适应
- `[768,992)`  : 类似 Pad 的分辨率  ： 默认 750
- `[992,1200)` : 中等屏幕的分辨率 ： 默认 970
- `[1200,*)`   : 电脑的分辨率 ： 默认 1170

### 两种容器
- container-fluid 
	- 流体布局 ： 平铺整个页面。 默认左右是有空隙的。
        ```
        .container-fluid {
            padding-right: 15px;
            padding-left: 15px;
            margin-right: auto;
            margin-left: auto;
        }
        
        ```
- container 
	- 固定布局 ： 左右两边分别有一定空隙。

    -  容器 与 阈值
		- 1170
        ```
        @media (min-width: 1200px)   bootstrap.css:1602
        .container {
            width: 1170px;
        }
        
        ```
		- 970
    		```
            @media (min-width: 992px)    bootstrap.css:1597
            .container {
                width: 970px;
            }
    
            ```
		- 750
    		```
    		@media (min-width: 768px)   bootstrap.css:1592
    		.container {
    			width: 750px;
    		}
    		
    		```
		- auto : 在 小于 768 时，自适应。 （可以放大页面获得该效果）
            ```
            .container {
                padding-right: 15px;
                padding-left: 15px;
                margin-right: auto;
                margin-left: auto;
            }
            
            ```

#### 语法 
- `*` 代表 [1,12] 间的整数， 页面缩放 可查看到不同的效果。
    - `col-lg-*` ： 大屏幕 `[1200,*)`
    - `col-md-*` ： 中等屏幕 `[992,1200)`
    - `col-sm-*` ：小屏幕 ， 如 pad `[768,992)`
    - `col-xs-*` : 移动端 范围 `[0  ,768)`

- 组合模式 （水平显示 到 垂直显示有一定的过渡）
    - 实例 ： 中文 BS 官网的 {Bootstrap相关优质项目推荐}
        ```
            <div class="row">
            	<div class="col-lg-4 col-md-6">col-lg-4 col-md-6</div>
                <div class="col-lg-4 col-md-6">col-lg-4 col-md-6</div>
                <div class="col-lg-4 col-md-6">col-lg-4 col-md-6</div>
            </div>
        
        ```

- Tips: 
    - 当 row 中的内容 不足 12 时 , 剩下的空间不会填充。
    - 当 row 中的内容 > 12 , 超出部分会进入下一行

    - 指定的 class 在小于所属的分辨率范围时，**水平显示** 会切换到 **垂直显示**。
    （如 3 个 `col-lg-4` 在 > 1200 时正常显示 ，（页面缩放，） <1200 时， 会显示成 3 行。）
    
    - 组合模式，水平 到 垂直 有一定的过渡
    
- Tips 动画示例
    ![](./ReadMe.image/row_split_12_cols.png)
    ![](./ReadMe.image/horizontal_to_vertical.gif)
    ![](./ReadMe.image/animation_while_horizontal_vertical.gif)

#### 示例 ：模仿 bootcss.com {Bootstrap相关优质项目推荐} 版块
    ![](./ReadMe.image/bootcss.com.simulation.gif)




###其他语法 （列偏移、列排序、消除浮动）
- 列偏移
    ```
    col-[*]-offset-*
    ```
- 列排序
    ```
    col-[*]-push-*
    col-[*]-pull-*
    ```
    - `pull-left` 靠左， `pull-right` 靠右。（见 **响应式布局**）
- 嵌套
- 清除浮动浮动



### 响应式工具
- 概念
    - 针对不同设备展示或隐藏页面内容
    
- 可见性
    - 实例 ： http://v3.bootcss.com/css/ 右侧的 导航 在分辨率较小时 隐藏。
    - `visible-*1-*2`
        1. `lg`、`md`、`sm`、`xs`
        2. `block`、`inline`、`inline-block`
    - `hidden-*`

    - 实例 ： 天猫侧边栏（右侧 我的收藏 等，通过 JS 控制，boot里面也可以实现。）
    
- 打印类
    - `visible-print-*`
    - `hidden-print`
    


### 6. Glyphicons 字体图标（组件） （图标不用图片，而是用字体）
- 好处
    - 减少请求
    - 容易控制样式
    - 例子 ： 淘宝首页的 充话费 等图标
- 用法
    - `font-face`
    - 字体路径
- 自制图标
    1. 如何把你的图标转换成web字体 http://jingyan.baidu.com/article/f79b7cb346cf499145023e78.html
    2. 参考 bootstrap.css 中 （关键字：@font-size 及 之后 的 glyphicon 系列）
        - 每个字体图标都有一个对应的编码。


### 7. 预定义样式
- default (默认样式)
- primary ( 首选项 ） 
- success （ 成功 ）
- info （ 一般消息 ）
- warning ( 警告 )
- danger （ 危险 ）

- 实例 ： 登录框


### 8. 按钮
- 基类 ： `btn`
- 样式
    - `btn-default` (默认)
    - `btn-link` (链接)
- 大小
    - `btn-*[lg|sm|xs]`
- 状态
    - `active`
    - `disable`

- 种类
    - a 、 input 、 button
- 块级
    - btn-block
- 按钮组
    - btn-group
    - btn-group-justified
    - btn-group-vertical
- 实例 ： github 按钮组


