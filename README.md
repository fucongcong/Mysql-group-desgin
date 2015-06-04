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

#对每个表进行字段的设计

##user表

字段|说明
:---------------|:---------------
id|主键
username|用户名
sex|性别
about|个人介绍

##groups表

字段|说明
:---------------|:---------------
id|主键
title|小组名
about|小组介绍
logo|logo的地址
ownerId|组长id
createdTime|创建时间

##groups_member表

字段|说明
:---------------|:---------------
id|主键
groupId|小组id
userId|用户id
role|角色[ owner、admin、member ]
createdTime|加入时间

##groups_thread表

字段|说明
:---------------|:---------------
id|主键
title|话题
content|话题内容
userId|发话题人
groupId|所属小组
createdTime|发帖时间

