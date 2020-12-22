# WS 事件协议

## `position` 位置

```json
{
  "lng": "30",
  "lat": "110",
  "elevation": "10",
  "tail": "10",
  "user_id": 1,
  "timestamp": 1577958298,
  "position_type": "Q",
  "qx_type": 2
}
```

字段解释：

```
lng：经度
lat：纬度
elevation：海拔
tail：净高
user_id：用户 ID
atimestamp：时间戳
position_type：定位类型
qx_type：千寻类型
```

## `user:status` 用户在线状态变化

> 只推送状态变化的用户

```json
{
  "user_id": 1,
  "status": "online"
}
```

`status` 字段枚举：

- `online`：上线
- `offline`：离线

## `user:info` 用户实时信息

> 定时推送所有用户的实时信息

```json
{
  "user_id": 1,
  "ip": "192.168.1.1",
  "battery": 88,
  "last_timestamp": 11111111111
}
```

## `group`

> 只推送组内状态变化的用户，非全部

```json
{
  "group_id": 11,
  "user": {
    "name": "user1",
    "status": "offline"
  }
}
```
