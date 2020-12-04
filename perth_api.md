
# 一、CONSTRAINT

## 1. Request
* URI: http://endpoint/api/v1/perth
* Content-Type: application/json
* Authorization: Bearer {token}

## 2. Response Format

Field   | Type  | Description
--------|-------|------------
return_code | **Int**     | 0-SUCCESS,1-Invalid_Request,2-SERVER_ERROR
message     | **String**  | "ok"-查询成功
data        | **JSON**    | 相关数据(对应API中的Response Body)

***

# 二、API

## 1. login user center

**PATH** `/login`

登录(注册)用户中心,不需要token

### Request Body

Field   | Type  | Description
--------|-------|------------
device_id    | **String**    | 设备ID
audience     | **String**    | app(商店ID)
os           | **String**    | 操作系统
device_model | **String**    | 设备型号

### Response Data

Field   | Type  | Description
--------|-------|------------
player_id   | **String**  | 玩家ID
token       | **String**  | 签名
expire      | **String**  | 过期剩余时间(秒)
freshman    | **Boolean** | 是否新用户

## 2. login game

**PATH** `/player/login`

登录游戏

### Request Body
No Request Body

### Response Data

Field   | Type  | Description
--------|-------|------------
id       | **String**  | 玩家ID
name     | **String**  | 玩家昵称
avatar   | **String**  | 头像ID

## 3. create game role

**PATH** `/player/create`

创建游戏角色

### Request Body

Field   | Type  | Description
--------|-------|------------
name    | **String**    | 玩家昵称
avatar  | **Int**       | 头像ID

### Response Data

Field   | Type  | Description
--------|-------|------------
id       | **String**  | 玩家ID
name     | **String**  | 玩家昵称
avatar   | **String**  | 头像ID

## 4. change name 

**PATH** `/player/name`

修改昵称

### Request Body

Field   | Type  | Description
--------|-------|------------
name    | **String**    | 玩家昵称

### Response Data

Field   | Type  | Description
--------|-------|------------
id       | **String**  | 玩家ID
name     | **String**  | 玩家昵称
avatar   | **Int**  | 头像ID

## 5. change avatar 

**PATH** `/player/avatar`

修改头像

### Request Body

Field   | Type  | Description
--------|-------|------------
avatar    | **int**    | 头像ID

### Response Data

Field   | Type  | Description
--------|-------|------------
id       | **String**  | 玩家ID
name     | **String**  | 玩家昵称
avatar   | **String**  | 头像ID

## 6. save leaderboard score 

**PATH** `/player/score`

保存积分

### Request Body

Field   | Type  | Description
--------|-------|------------
score   | **Double** | 积分

### Response Data
No Response Data

## 7. get leaderboard 

**PATH** `/player/leaderboard`

保存积分

### Request Body
No Request Data

### Response Data
Field   | Type  | Description
--------|-------|------------
rank             | **Int**    | 排名
score            | **Double** | 积分
leaderboardItems | **LeaderboardItem[]**   | 榜单

LeaderboardItem
Field   | Type  | Description
--------|-------|------------
id      | **String** | 玩家ID
name    | **String** | 玩家昵称
avatar  | **Int**    | 头像ID
rank    | **Int**    | 排名
score   | **Double** | 积分


## 7. get init config 

**PATH** `/init/config`

获取初始配置数据

### Request Body
No Request Data

### Response Data
Field   | Type  | Description
--------|-------|------------
isAppStoreReview  | **Boolean** | 是否appStore提审版本

