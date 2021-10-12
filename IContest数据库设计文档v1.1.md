# 数据库设计文档

**数据库名：** icontestdb

**文档版本：** 1.1

**文档描述：** IContest数据库设计文档v1.1

| 表名                  | 说明       |
| :---: | :---: |
| [collection](#collection) |  |
| [contest](#contest) |  |
| [contest_board](#contest_board) | 竞赛活动公告栏 |
| [reply](#reply) |  |
| [sys_role](#sys_role) | 角色信息表 |
| [sys_user](#sys_user) |  |
| [team](#team) |  |
| [team_user](#team_user) |  |
| [topic](#topic) |  |

**表名：** <a id="collection">collection</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | user_id |   int   | 10 |   0    |    Y     |  N   |       | 外键，用户id  |
|  3   | obj_id |   int   | 10 |   0    |    Y     |  N   |       | 收藏对象id，可以是contest或topic  |
|  4   | create_time |   timestamp   | 19 |   0    |    Y     |  N   |       |   |
|  5   | update_time |   timestamp   | 19 |   0    |    Y     |  N   |       |   |

**表名：** <a id="contest">contest</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | title |   varchar   | 255 |   0    |    Y     |  N   |       | 标题  |
|  3   | digest |   varchar   | 255 |   0    |    Y     |  N   |       | 摘要  |
|  4   | url |   varchar   | 255 |   0    |    Y     |  N   |       | 原文链接url  |
|  5   | cover_url |   varchar   | 255 |   0    |    Y     |  N   |       | 封面图片url  |
|  6   | gmt_create |   datetime   | 19 |   0    |    Y     |  N   |       | 创建时间  |
|  7   | gmt_modified |   datetime   | 19 |   0    |    Y     |  N   |       | 修改时间  |
|  8   | type |   tinyint   | 3 |   0    |    Y     |  N   |       |   |

**表名：** <a id="contest_board">contest_board</a>

**说明：** 竞赛活动公告栏

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | contest_id |   int   | 10 |   0    |    Y     |  N   |       |   |
|  3   | content |   varchar   | 255 |   0    |    Y     |  N   |       | 公告内容  |
|  4   | title |   varchar   | 255 |   0    |    Y     |  N   |       | 公告标题  |
|  5   | user_id |   int   | 10 |   0    |    Y     |  N   |       |   |
|  6   | create_time |   timestamp   | 19 |   0    |    Y     |  N   |       |   |
|  7   | update_time |   timestamp   | 19 |   0    |    Y     |  N   |       |   |

**表名：** <a id="reply">reply</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | topic_id |   int   | 10 |   0    |    N     |  N   |       | 回复主题帖id  |
|  3   | reply_user_id |   int   | 10 |   0    |    N     |  N   |       | 用户id  |
|  4   | to_reply_id |   int   | 10 |   0    |    Y     |  N   |   0    | 回复的评论id，若为回复主题帖则置0  |
|  5   | content |   text   | 65535 |   0    |    Y     |  N   |       |   |
|  6   | create_time |   timestamp   | 19 |   0    |    Y     |  N   |       |   |
|  7   | update_time |   timestamp   | 19 |   0    |    Y     |  N   |       |   |

**表名：** <a id="sys_role">sys_role</a>

**说明：** 角色信息表

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   bigint   | 20 |   0    |    N     |  Y   |       | 角色ID  |
|  2   | role_name |   varchar   | 30 |   0    |    N     |  N   |       | 角色名称  |
|  3   | role_key |   varchar   | 100 |   0    |    N     |  N   |       | 角色权限字符串  |
|  4   | status |   tinyint   | 4 |   0    |    N     |  N   |       | 角色状态（0正常1停用）  |
|  5   | is_deleted |   tinyint   | 4 |   0    |    Y     |  N   |   0    | 删除标志（0代表存在1代表删除）  |
|  6   | create_by |   varchar   | 64 |   0    |    Y     |  N   |       | 创建者  |
|  7   | remark |   varchar   | 500 |   0    |    Y     |  N   |       | 备注  |
|  8   | gmt_create |   datetime   | 19 |   0    |    Y     |  N   |       | 创建时间  |
|  9   | gmt_update |   datetime   | 19 |   0    |    Y     |  N   |       | 更新时间  |

**表名：** <a id="sys_user">sys_user</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       | 用户表主键  |
|  2   | username |   varchar   | 255 |   0    |    Y     |  N   |       | 用户名  |
|  3   | password |   varchar   | 255 |   0    |    Y     |  N   |       | 密码  |
|  4   | email |   varchar   | 255 |   0    |    Y     |  N   |       | 邮箱  |
|  5   | qq |   varchar   | 20 |   0    |    Y     |  N   |       | qq号  |
|  6   | credit |   int   | 10 |   0    |    Y     |  N   |       | 积分  |
|  7   | avatar |   varchar   | 255 |   0    |    Y     |  N   |       | 头像url  |
|  8   | gmt_create |   datetime   | 19 |   0    |    Y     |  N   |       | 创建时间  |
|  9   | gmt_modified |   datetime   | 19 |   0    |    Y     |  N   |       | 修改时间  |

**表名：** <a id="team">team</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | name |   varchar   | 255 |   0    |    Y     |  N   |       | 队伍名称  |
|  3   | type |   varchar   | 255 |   0    |    Y     |  N   |       | 队伍类型  |
|  4   | info |   varchar   | 255 |   0    |    Y     |  N   |       | 队伍信息  |
|  5   | gmt_create |   datetime   | 19 |   0    |    Y     |  N   |       | 创建时间  |
|  6   | gmt_modified |   datetime   | 19 |   0    |    Y     |  N   |       | 修改时间  |

**表名：** <a id="team_user">team_user</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | team_id |   int   | 10 |   0    |    Y     |  N   |       | team表的id  |
|  3   | user_id |   int   | 10 |   0    |    Y     |  N   |       | user表的id  |
|  4   | username |   varchar   | 255 |   0    |    Y     |  N   |       | 用户名，冗余  |

**表名：** <a id="topic">topic</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   int   | 10 |   0    |    N     |  Y   |       | 帖子ID  |
|  2   | user_id |   int   | 10 |   0    |    N     |  N   |       | 发帖人id  |
|  3   | title |   varchar   | 200 |   0    |    Y     |  N   |       | 标题  |
|  4   | content |   text   | 65535 |   0    |    Y     |  N   |       | 内容  |
|  5   | click |   int   | 10 |   0    |    Y     |  N   |   0    | 点击量  |
|  6   | tab |   varchar   | 100 |   0    |    Y     |  N   |       | 标签类型  |
|  7   | gmt_create |   datetime   | 19 |   0    |    Y     |  N   |       | 创建时间  |
|  8   | gmt_modified |   datetime   | 19 |   0    |    Y     |  N   |       | 修改时间  |
