![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Find Database, Size, Data, Log, And Filepaths With SQL
**Post Date: July 10, 2017**





## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process


<p>Here's some simple logic to get you the database name, data, log, size, and file path for all your data files.</p>

![Find Database Details With SQL]( https://mikesdatawork.files.wordpress.com/2017/07/image0011.png "Find Database Details With SQL")
 
    
## SQL-Logic
```SQL
use master;
set nocount on
 
select
    [database]  = db_name(smf.database_id)
,   [file_id]
,   [type]      = (case [type] when 0 then 'data' when 1 then 'log' when 2 then 'filestream' when 4 then 'fulltext' end)
,   [logical_name]  = smf.name
,   [physical_name]
,   [size]  =   ( 
                case
                    when smf.size * 8 / 1024 / 1024 < 1 then cast(smf.size * 8 / 1024 as varchar) + ' MB'
                    when smf.size * 8 / 2014 / 1024 > 0 then cast(smf.size * 8 / 1024 /1024 as varchar) + ' GB'
                end
                )
from
    sys.master_files smf
order by
    smf.size desc
```
 


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

   
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

