<!-----
title:  "获取权限无UIAlert提示的bug处理"
date:   2016-01-14 17:29:01
---
-->
1. 确认 targets - bundle setting - bundle name 是否与设备(或模拟器)中其他应用冲突, 导致权限信息无法获取.

2. 确认 targets - bundle setting 中是否包含 Bundle display name , 如果不存在, 则添加 并 设置 value 为 此应用桌面展示的名称.
