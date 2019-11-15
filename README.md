![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 检查AlwaysOn Primary的状态
#### Check For AlwaysOn Primary Status
**发布-日期: 2014年10月30日 (评论)**


## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
此SQL逻辑（logic）将帮助你检查你运行的实例是否是AlwaysOn配置中的Primary。

## English
This SQL logic will check to see if the instance you are running it on is the Primary in an AlwaysOn configuration.

---
## Logic
```SQL
declare @server_name 				varchar(255)
declare @availability_group_name 	varchar(255)
declare @check_if_primary 			varchar(255)
set 	@server_name 				= ( select cast(serverproperty('servername') as varchar(200)) )
set 	@availability_group_name 	= ( select name from sys.availability_groups )
set 	@check_if_primary 			= ( select sdhars.role_desc from sys.dm_hadr_availability_replica_states sdhars inner join sys.availability_groups sag on sdhars.group_id = sag.group_id where sag.name = @availability_group_name and sdhars.is_local = 1 )
 
if @check_if_primary = 'PRIMARY'
 	begin
 		print 'This Server: ' + @server_name + ' (IS) the PRIMARY'
 	end
 	else
 		print 'This Server: ' + @server_name + ' (IS NOT) the PRIMARY'


```


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

