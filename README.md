# Mysql-group-desgin
简单的小组功能进行表结构的设计

访问[www.xitongxue.com观看课程](http://xitongxue.com)
关注我们的ＱＱ群：390536187

#基础需求

###用户可以创建小组，用户加入小组后可以在小组中发帖，回帖。
###小组要包括　标题、内容、logo、小组组长、创建时间。
###小组中一共可以分为（组长，副组长，组员）三种角色。

#需要创建的表

表名|说明
:---------------|:---------------
user|用户信息
groups|小组信息
groups_member|小组成员
groups_thread|小组话题
groups_thread_post|话题回复

#对每个表进行字段的设计

##user表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
username|用户名|varchar(255)
sex|性别|enum('male','femal')
about|个人介绍|text

##groups表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
title|小组名|varchar(255)
about|小组介绍|text
logo|logo的地址|varchar(255)
ownerId|组长id|int
createdTime|创建时间|datetime

##groups_member表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
groupId|小组id|int
userId|用户id|int
role|角色[ owner、admin、member ]|enum('owner','admin','member')
createdTime|加入时间|datetime

##groups_thread表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
title|话题|varchar(255)
content|话题内容|text
userId|发话题人|int
groupId|所属小组|int
createdTime|发帖时间|datetime


##groups_thread_post表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
content|回复内容|text
threadId|回复话题Id|int
userId|回复人Id|int
createdTime|回复时间|datetime


#插入一些数据

#进行相应需求的查询练习

##查询所有小组
##统计每个小组中的话题数与成员数


