# R语言习题集[^1]
[^1]:说明：所有命令，在github文档中，应当放在``（数字1左边的键）符号中

## 一、数据输入（10分）
### 请将下表在R中输入成data frame的格式，命名为prac01。

|*ID*|*Major*|*mid*|*final*|*total*|*Male*|
|:---:|:---:|:---:|:---:|:---:|:---:|
|1|英语|83|85|84|TRUE|
|2|法语|88|84|86|TRUE|
|3|社会工作|82|86|84|FALSE|
|4|应用心理学|89|88|88|FALSE|
|5|应用心理学|86|86|86|TRUE|
### 答案：
★(1511105 商美）  
***




## 二、命令练习（20分）
###  (一)在#号后面解释前述命令的功能

`seq(1, 20, by = 2) #`  

`LETTERS[1:5] #`  

`letters[5:1] #`  

`rep(LETTERS[1:3], each = 3) #`  

`rep(LETTERS[1:3], times = 3) #`  

`dnorm(-2, 10, 2) #`  

`pnorm(-2, 10, 2) #`  

`pnorm(2.5)-pnorm(2) #`  

`rnorm(10, 20, 5) #`  

`qnorm(0.25, 10, 2) #`  
`cbind(dataA, dataB) #`  

`rbind(data, dataB) #`  

`quantile(x, probs = c(0.1, 0.6, 0.9) #`  

`scale(x, center = T, scale = T) #`  

`min(x) #`  

`max(x) #`  

`mean(x) #`  

`sd(x) #`  

`median(x) #`  

`cor(x, y) #`  

`IQR(x) #`  

`choose(n, k) #`  

`summary(x) #`  

`factorial(n) #`  

`fivenum(x) #`  

`options(digits = 5) #`  

`var(x) #`  

`round(x) #`  

`choose(10, 6) * factorial(6) #`
(1512894 尚灵)  
***

###  (二)总结Hadley Wickham开发的readxl和haven包中的常用文件导入函数，可参考其个人网页整理。

###  [http://hadley.nz/](http://hadley.nz/)

## 三、数据操纵（30分）

###  (一)安装readxl包，读入rs2015.xlsx文件，取名为rs2015。该文件为2015年选修《R语言统计应用入门》的所有同学的期中成绩（mid）和期末成绩（final）。写出读入命令的语句，并结合dplyr包完成以下任务：
（1512881 司可一）  
***

#### （1）生成新变量“总评成绩”（total），其计算公式为期中成绩的40%，加上期末成绩的60%。注意总评成绩需要四舍五入为整数。
#### （2）生成新变量“等级成绩”（rank），取值方式如下：

|   总评成绩（total）|     等级成绩（rank）    | 
| :-----------------: |:----------------------:| 
|           90~100         |                   A                   |
|          80~89            |                   B                   |  
|          70~79            |                    C                  |  
|          60~69           |                    D                  |
|            0~59            |                    E                  |

(1512890黄子晴)

***  

### （3）生成新的虚拟变量psy，凡是原文件中major为PSY的取值为1
### （4）所有结果，先按psy变量升序排序，再按total变量降序排序。
### （5）将上述结果写出为新的.csv文件，命名为 *rs2015_arranged.csv* 。
### （6）无放回地从心理学和非心理学的同学中，各自随机抽取5名同学，结果命名为 *samples_by_psy* 。
### （7）选出所有major为PSY的同学，另存为一个新数据框，命名为 *psystudents* 。  

### 答案：
(1512891 李晟雪)
***

### &emsp;&emsp;（二）数据*PDSurveyBasic.xlsx*是南开大学汪新建教授主持的《医患信任建设的社会心理机制研究》这一项目中《医患社会心态问卷：患方卷》的部分试调查数据，该数据使用问卷星平台获得，下载*Excel*格式后我们将部分基础信息提取保存，并将变量名改为英文。部分数据显示如下：  
|*ID*|*Time1*|*Time2*|*IP*|*Relationship*|*Student*|
|:---:|:---:|:---:|:---:|:---:|:---:|
|8|2017/4/30 17:47:48|42秒|36.111.130.24(内蒙古-呼和浩特)|3|1|
|9|2017/4/30 18:41:02|3130秒|36.111.130.24(内蒙古-呼和浩特)|4|2|
|10|2017/4/30 20:08:23|1559秒|124.31.6.128(西藏-拉萨)|5|2|
|11|2017/4/30 20:08:49|1540秒|124.31.6.128(西藏-拉萨)|5|2|
|12|2017/4/30 20:09:12|926秒|106.57.158.22(云南-丽江)|3|2|
|13|2017/4/30 20:19:47|30秒|220.115.23.8(天津-天津)|5|1|
|14|2017/4/30 20:20:56|65秒|220.115.23.8(天津-天津)|5|1|
|15|2017/4/30 20:32:17|965秒|106.57.158.22(云南-丽江)|2|2|
|16|2017/4/30 20:37:46|2955秒|123.54.168.84(河南-信阳)|2|	2|
 
  
~~★(1512898张雪丽)~~
***
### 其中各变量的说明如下：
#### id：指问卷提交顺序；
#### time1：指问卷提交的时刻，采用北京时间年/月/日/时/分/秒的标准化格式；
#### time2：指完成问卷的全部用时；
#### ip：被试的手机ip或调查员的手机ip，因为使用的学生访问员，用自己的手机一对一对被试进行问卷呈现（主要针对中老年被试），或者发送链接由被试独立完成，因此每一ip可能出现多次，但仍代表着不同被试。
#### relationship：该题目对应原始问卷的如下题目：
### 1. 您与医务人员的关系是：
#### **①** 我是在医院工作的医务人员（医生、护士、医院行政管理人员等）或医学院（包括卫生职业学校）的教师
#### **②** 我有直系亲属（此处意指爱人、子女、父母、兄弟姐妹、祖父母外祖父母）是医务人员


(1512879米尔迪）
***  
####  **③** 我有关系密切的朋友是医务人员
####  **④** 我有一般亲属或朋友是医务人员
####  **⑤** 我和我身边的亲属朋友没有是医务人员的  

 * 因本问卷为患方卷，因此，拟排除医务人员，即有效患方被试**应当是选择数字1之外的被试。**
 * student:被试是否仍然是学校（包括初高中、中专、大学专科、本科或研究生）的**全日制在读学生**。  
   &emsp;&emsp；**1** = 是 ， **2** = 不是  
 * 本研究拟排除学生被试，因其疾病经历较为有限。

#####  注：编制者在试调查之前已找少部分被试进行了预调查，估计较为认真作答的被试，一般应至少有10分钟左右方可填完问卷。被试的回答时间集中于20~30分钟以内，除了极少数老年被试，一般回答时常不会超过60分钟。


（1511411 白博仁）





