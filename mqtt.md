# Mqtt topic

## 修改记录

- `2020-12-22#2`：去除心跳包 ip
- `2020-12-22#1`：重构 tenant topic 
- `2020-12-22#0`：MQTT 协议第一版

## 消息

| topic         | 说明 |
|---------------|----|
| info/heart, info/$tenantId/heart       | 心跳 |
| info/position, info/$tenantId/position | 位置 |
| info/up, info/$tenantId/up             | 上线 |
| info/down, info/$tenantId/down         | 遗嘱 |
| info/alarm, info/$tenantId/alarm       | 报警 |

### info/heart, info/$tenantId/heart

```json
{
  "user_id": 1,
  "tenant_id": 1,
  "timestamp": 1608618462,
  "battery": 80,
  "battery_charging": false,
  "mode": "NORMAL",
  "network": "4G"
}
```

### info/position, info/$tenantId/position

```json
{
  "user_id": 1,
  "tenant_id": 1,
  "timestamp": 1608618462,
  "lng": 122.23333,
  "lat": 43.23333,
  "elevation": 10,
  "position_type": "Q",
  "qx_type": 1
}
```

### info/up, info/$tenantId/up

```json
{
  "user_id": 1,
  "tenant_id": 1,
  "timestamp": 1608618462,
  "lng": 122.23333,
  "lat": 43.23333
}
```

### info/down, info/$tenantId/down

```json
{
  "user_id": 1,
  "tenant_id": 1
}
```

### info/alarm, info/$tenantId/alarm

```json
{
  "user_id": 1,
  "tenant_id": 1,
  "timestamp": 1608618462,
  "lng": 122.23333,
  "lat": 43.23333,
  "alarm_type": "SOS",
  "additional": ""
}
```

## 操作

| topic              | 说明   |
|--------------------|------|
| op/alarm/cap/$id   | 下发报警 |
| op/command/cap/$id | 下发命令 |

### op/alarm/cap/$id

```json
{
  "alarm_type": "SOS"
}
```

### op/command/cap/$id

```json
{
  "command": "shot"
}
```

`command` 字段枚举：

- `shot`：拍照
- `video`：录像
- `video:off`: 关闭录像
- `update`：拉取配置
- `interphone:on`: 对讲机开启
- `interphone:off`：对讲机关闭
- `interphone:shot`：对讲机模式拍照
- `interphone:video:on`：对讲机模式录像
- `interphone:video:off`：对讲机模式关闭录像
- `mode:switch:interphone`: 切换对讲机
- `mode:switch:normal`: 切换正常
