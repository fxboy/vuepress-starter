---
title: 操作对象
lang: zh-CN
---
# 操作对象
操作对象是框架中所含有的entity包下的对象类，到1.3.6 仅有一个 Authentications 对象
## Authentications

### 属性
|属性        |类型                            |注释                             |
|:----------|:-------------------------------|:-------------------------------|
|*value*  |HashMap<String,T>|用来保存（key）role和（value）permission |

:::warning
permission 只支持 String,String[],还有 ArrayList< String > 三种对象类型
:::
### 方法

#### add
向对象内添加角色和操作权限
|属性        |类型                            |注释                     |
|:----------|:-------------------------------|:-----------------------|
|*role*  | String | 角色名称
|*premissions*  | String,String[] or ArrayList< String > | 操作权限列表或单个操作权限


#### hasRole
用来获取当前对象中所有匹配路径权限(controller中的权限校验的注解)的角色
|属性        |类型                            |注释                     |
|:----------|:-------------------------------|:-----------------------|
|*roles*  | List | 注解上设置的角色，或手动添加的角色|

##### 返回
|类型        |返回内容                            |
|:----------|:-------------------------------|
|*List*  | 所有匹配的role列表

#### hasAllPermission
校验某个用户的操作权限是否与注解上定义的操作权限完全匹配，比如说有 select,delete权限，则用户的权限必须要包含这两个权限
|属性        |类型                            |注释                     |
|:----------|:-------------------------------|:-----------------------|
|*permissions*  | List | 注解上设置的操作权限，或手动添加的操作权限|
|*role*  | String | 要取出某个角色的操作权限|

##### 返回
|类型        |返回内容                            |
|:----------|:-------------------------------|
|*boolean*  | 是否匹配

#### hasAnyPermission
校验某个用户的操作权限是否与注解上定义的操作权限有一个匹配，比如说有 select,delete权限，则用户的权限只需要有一个权限匹配即可

|属性        |类型                            |注释                     |
|:----------|:-------------------------------|:-----------------------|
|*permissions*  | List | 注解上设置的操作权限，或手动添加的操作权限|
|*role*  | String | 要取出某个角色的操作权限|
##### 返回
|类型        |返回内容                            |
|:----------|:-------------------------------|
|*boolean*  | 是否匹配

一切就是这么的简单！具体请看 DOC-API

