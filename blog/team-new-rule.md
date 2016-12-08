<!--
author: rickeryu
date: 2016-11-08
title: WEB端PHP开发基本要求整理
tags: Web,PHP,要求
category: 新手教程
status: publish
summary: 
WEB开发PHP基本要求整理。
-->

##环境版本

1. 开发工具 PHPStorm 2016.2  
2. PHP版本 PHP5.5及PHP5.5以上   
3. MYSQL版本 MYSQL5.6 

###win平台本地环境搭建
[参考链接](#)  

###mac平台本地环境搭建
[参考链接](http://toutiao.com/i6325907843597730305/)


##版本管理git或svn 
1. 公司常用svn工具（svn账号找于志远开通），但针对于不同的客户有可能会用到git，所以要求熟悉svn与git的操作    
2. git完成对应文档的任务（git任务文档.doc）->git的基本操作 [git参考链接](http://www.bootcss.com/p/git-guide/)




##编码规范
方法名称   
1. 统一使用小写字母比如index,course等，如一个单词不能表达使用驼峰couseIndex这种   

方法参数   
1. 更新操作 ($map,$data),第一个条件，第二个为数据    
2. 添加操作 ($data) ,每一个为数据   
3. 查询操作 ($map,$field,$order,$limit,$iscache)，第一个条件，第二个显示列，第三个排序，第四的数量，不一定全部要有，但要有按顺序   
4. 删除操作 ($map)，第一个为条件 

方法注释   
```
/**
 * 方法作用描述
 * @name: demo
 * @param array $map
 * @param array $data
 * @return void
 * @author: 作者名 <作者邮件>
 * @time: 添加时间
 */
```  
PHPStorm配置变量 Editor->File and Code Templates-> PHP Function Doc Comment
```
/**
 * ${CARET}
 * @name: ${NAME}
 ${PARAM_DOC}
 * @return ${TYPE_HINT}
 * @author: rickeryu <lhyfe1987@163.com>
 * @time:
 */
```

##模板命名
一个单词方法名与模板名相同，比如index->index.html，多个单词用_分隔，比如courseIndex->course_index.html

##返回值判断
1. 在返回值的地方，一定要判断null的情况,推荐放到Model里面   
2. 由于历史原因，数据库的列存在大小写的问题，插入数据或更新数据一定要确认   
