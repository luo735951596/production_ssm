# 欢迎报bug或pull request ~

# production_ssm

这是一个生产管理ERP系统。依托科技计划重点项目“制造装备物联及生产管理系统研发”，主要包括：计划进度、设备管理、工艺监控、物料监控、人员监控、质量监控、系统管理7大模块。


## 项目技术架构(Spring+SpringMVC+Mybatis） ##
- Maven
- Spring（IOC DI AOP 声明式事务处理）
- SpringMVC（支持Restful风格）
- Hibernate Validator（参数校验）
- Mybatis（最少配置方案）
- shiro权限控制,结合ajax实现了异步认证与异步授权，同时实现了细粒度的权限动态分配（到按钮级别）
- jQuery EasyUI开发前端页面，利用jQuery文件上传插件实现拖拽上传的效果并对文件类型、大小、数量进行控制；利用search-box实现查找功能
- [Druid（数据源配置 sql防注入 sql性能监控)](http://wosyingjun.iteye.com/blog/2306139)
- 统一的异常处理
- JSP JSTL JavaScript
- kindeditor富文本编辑器，处理图片上传和富文本编辑<!--more-->

## 系统架构 ##

![系统架构图](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E9%25A1%25B9%25E7%259B%25AE%25E6%259E%25B6%25E6%259E%2584.png)

## 数据库设计（详见sql文件） ##

![数据库设计](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E6%2595%25B0%25E6%258D%25AE%25E5%25BA%2593%25E8%25AE%25BE%25E8%25AE%25A1.png)

## 软件运行截图 ##

- **登录界面**

![登录界面](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E7%2599%25BB%25E5%25BD%2595%25E7%2595%258C%25E9%259D%25A2.png)

- **运行界面**

![运行界面](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E8%25BF%2590%25E8%25A1%258C%25E7%2595%258C%25E9%259D%25A2.png)

- **图片上传**

![图片上传](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E5%259B%25BE%25E7%2589%2587%25E4%25B8%258A%25E4%25BC%25A0.png)

- **文件上传**

![文件上传](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E6%2596%2587%25E4%25BB%25B6%25E4%25B8%258A%25E4%25BC%25A0.png)

- **富文本编辑**

![富文本编辑](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E5%25AF%258C%25E6%2596%2587%25E6%259C%25AC%25E7%25BC%2596%25E8%25BE%2591.png)

- **关联信息**

![关联信息](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E5%2585%25B3%25E8%2581%2594%25E4%25BF%25A1%25E6%2581%25AF.png)

- **search-box查找**

![search-box查找](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/search-box%25E6%259F%25A5%25E6%2589%25BE.png)

- **动态权限控制**

![动态权限控制](http://coding.net/u/megagao/p/ziyuan/git/raw/master/pm_image/%25E5%258A%25A8%25E6%2580%2581%25E6%259D%2583%25E9%2599%2590%25E6%258E%25A7%25E5%2588%25B6.png)

## 注： ##

**文件上传配置**

在本地建立上传图片和文件的文件夹，如我的存放路径是在D:\upload\temp\img，D:\upload\temp\file文件夹下，然后修改tomcat的配置文件server.xml，添加虚拟路径，将对图片和文件的请求url映射到本机硬盘的相应路径，如下：

	<Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">
        <!-- SingleSignOn valve, share authentication between web applications
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.authenticator.SingleSignOn" />
        -->

        <!-- Access log processes all example.
             Documentation at: /docs/config/valve.html
             Note: The pattern used is equivalent to using pattern="common" -->
        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />

        <!-- 在Host标签下添加下面两行，配置虚拟路径到你本机的文件夹 -->
        <Context path="/pic" docBase="D:\upload\temp\img" crossContext="true" trusted="true" reloadable="true"/>
        <Context path="/file" docBase="D:\upload\temp\file" crossContext="true" trusted="true" reloadable="true"/>
	</Host>

**idea classpath配置**

idea引入项目后，resources目录在eclipse中是在classpath下的，而在idea中变成在classpath外，导致项目无法识别配置文件。解决办法是把resources文件夹加入到classpath中，请参照此博文操作：[http://blog.csdn.net/kesarchen/article/details/51193657](http://blog.csdn.net/kesarchen/article/details/51193657)