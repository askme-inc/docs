# Mqtt topic

## 修改记录

- `2020-12-22`：MQTT 协议第一版

## 消息

| topic         | 说明 |
|---------------|----|
| info/heart    | 心跳 |
| info/position | 位置 |
| info/up       | 上线 |
| info/down     | 遗嘱 |
| info/alarm    | 报警 |

### info/heart

```json
{
  "user_id": 1,
  "timestamp": 1608618462,
  "battery": 80,
  "mode": "NORMAL",
  "network": "4G",
  "ip": "192.168.1.1"
}
```

### info/position

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

### info/up

```json
{
  "user_id": 1,
  "tenant_id": 1,
  "timestamp": 1608618462,
  "lng": 122.23333,
  "lat": 43.23333
}
```

### info/down

```json
{
  "user_id": 1,
  "tenant_id": 1
}
```

### info/alarm

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
