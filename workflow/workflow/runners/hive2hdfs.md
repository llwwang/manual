**执行hive2hdfs导入任务**

### 功能说明
将hive sql 查询结果导入hdfs。

### 其他说明
不知道复杂的查询sql ，如果有复杂的统计查询，可以用先执行 hive sql 脚本任务，将查询结果写入hive 表，然后再将结果表记录通过 hive导入hdfs 任务写入hdfs 。 

### 任务设置
#### 1. 基本信息  
参考 [基本信息设置](/workflow/workflow/runnerBasicInfo.md)  
#### 2. 调度  
参考 [调度设置](/workflow/workflow/runnerCycle.md)  

#### 3. 参数
任务配置参考：
![hive2hdfs](/workflow/workflow/images/hive2hdfs.png)

###### 3.1 源服务器
执行hive sql 查询语句所在的hive server  
更多信息参考 [服务器配置](/workflow/services/readme.md)
###### 3.2 目标服务器
存储最终结果所在的HDFS server   
更多信息参考 [服务器配置](/workflow/services/readme.md)
###### 3.3 DB名称
指定查询sql 所在hive db库  

###### 3.4 源SQL
hive sql 查询语句  
支持[时间隐式参数](/workflow/more/implicitVariable.md)

###### 3.5 源SQL查询结果字段数量（可选）
对于稍微复杂的查询，可能会出现无法识别查询结果的字段个数，需要特别指定查询结果字段个数。  
select * 这种查询结果可以识别，不用担心。  
如果用户不指定的情况下，会使用系统识别到的结果个数，如果用户指定了查询结果字段个数，则优先使用用户指定的查询结果个数。

###### 3.6 目标目录
查询结果存放HDFS路径

##### 3.7 对账目录
通过确保对账文件内容和目标目录数据文件一致，确定数据入库完成，切数据没有丢失。
##### 3.8 对账文件名
对账文件名称

##### 3.9 目标文件分隔符
数据落地到hdfs 数据，用来切分字段结果。
##### 3.10 beeline输出格式
hive beeline 命令行的输出格式，基于4.0.3.1 的hive 采用默认值 **Output:**
##### 3.11 hive参数
用来支持非tbds 集群安装的hive 集群，可能需要的特殊参数

### demo
参考上图

### demo资源
