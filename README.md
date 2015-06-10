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
##创建一个用户
	
	insert into user(username,sex,about) values ('小王','male','一个大学生'),
	('小李','male','一个小学生'),
	('小舞','female','一个中学生'),
	('小舞2','female','一个中学生'),
	('小舞3','female','一个中学生'),
	('小舞4','female','一个中学生'),
	('小舞5','female','一个中学生'),
	('小舞6','female','一个中学生'),
	('小舞7','female','一个中学生'),
	('小舞8','female','一个中学生')

##创建小组
	
	insert into groups(title,about,ownerId,createTime)  values ('HTML小组','HTML是网站的基础语言',1,'2015-05-05 12:12:12'),
	('CSS小组','css布局',1,'2015-04-05 12:12:12'),
	('JS小组','js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组1','js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组2','js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组3','js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组4','js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组'5,'js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组6','js前端语言',1,'2015-06-05 12:12:12'),
	('JS小组7','js前端语言',1,'2015-06-05 12:12:12')

##加入小组

	insert into groups_member(groupId,userId,role,createdTime) values (1,1,'owner','2015-05-05 12:12:12'),
	(2,1,'owner','2015-04-05 12:12:12'),
	(3,1,'owner','2015-06-05 12:12:12'),
	(4,1,'owner','2015-06-05 12:12:12'),
	(5,1,'owner','2015-06-05 12:12:12'),
	(6,1,'owner','2015-06-05 12:12:12'),
	(7,1,'owner','2015-06-05 12:12:12'),
	(8,1,'owner','2015-06-05 12:12:12'),
	(9,1,'owner','2015-06-05 12:12:12'),
	(10,1,'owner','2015-06-05 12:12:12'),
	(4,2,'member','2015-07-05 12:12:12'),
	(1,3,'admin','2015-07-05 12:12:12'),
	(1,5,'member','2015-07-05 12:12:12'),
	(5,7,'member','2015-07-05 12:12:12'),
	(4,6,'member','2015-07-05 12:12:12'),
	(6,8,'member','2015-07-05 12:12:12'),
	(6,2,'member','2015-07-05 12:12:12'),
	(2,2,'member','2015-07-05 12:12:12'),
	(1,9,'member','2015-07-05 12:12:12'),
	(8,2,'member','2015-07-05 12:12:12'),
	(7,7,'member','2015-07-05 12:12:12'),
	(8,8,'member','2015-07-05 12:12:12'),
	(5,5,'member','2015-07-05 12:12:12'),

##发布一个话题


##回复一个话题

#尝试更新一些数据
##更新用户信息
##更新小组信息
##退出小组
##
#进行相应需求的查询练习

##查询所有小组

	select * from groups;

##查询指定小组下的话题（根据创建时间取前5条）

	select * from groups_thread where groupId = 1 order by createdTime DESC limit 5;

##查询指定话题下的回复数（根据回复时间取前5条）
	
	select * from groups_thread_post where threadId = 1 order by createdTime DESC limit 5

##查询一个小组中的成员
	
	select user.username from groups_member,user where groupId = 1 and groups_member.userId = user.id ;

##查询指定小组下的话题（根据回复数取前5条）



##查询近半月发布的话题分别按发布时间与回复数降序排列
##根据成员数对小组进行一个排名，取出前5个数据
##统计每个小组中的话题数与成员数

#对我们的数据表进行改进，增加统计字段

##groups表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
title|小组名|varchar(255)
about|小组介绍|text
logo|logo的地址|varchar(255)
ownerId|组长id|int
threadNum|话题数|int
memberNum|成员数|int
createdTime|创建时间|datetime

##groups_thread表

字段|说明|类型
:---------------|:---------------|:---------------
id|主键|int
title|话题|varchar(255)
content|话题内容|text
userId|发话题人|int
groupId|所属小组|int
postNum|回复数|int
createdTime|发帖时间|datetime

#在来写我们的查询语法

##查询近半月发布的话题分别按发布时间与回复数降序排列

##根据成员数对小组进行一个排名，取出前10个数据

##统计每个小组中的话题数与成员数





