# UDP 包协议

## 位置信息

包头：`[0x55, 0xaa]`

包体：

```json
{
  "lng": "30",
  "lat": "110",
  "elevation": "10",
  "tail": "10",
  "user_id": 1,
  "tenant_id": 1,
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
tenant_id: 租户 ID
timestamp：时间戳
position_type：定位类型
qx_type：千寻类型
```

## 上下线状态信息

包头：`[0x55, 0xae]`

包体：

```json
{
  "status": "up | down",
  "lng": 30.01,
  "lat": 110.01,
  "user_id": 1,
  "tenant_id": 1,
  "timestamp": 1577958298,
  "battery": 99,
  "mode": "NORMAL | TALK",
  "distance_sensor": 111.01,
  "network": "WIFI | 4G"
}
```

## 心跳

包头： `[0x55, 0xab]`

包体：

```json
{
  "user_id": 1,
  "tenant_id": 1,
  "battery": 99,
  "ip": "192.168.1.1",
  "distance_sensor": "111",
  "mode": "NORMAL | TALK",
  "network": "WIFI | 4G"
}
```

## 下发指令

包头：`[0x55, 0xac]`

包体：

```json
{
  "command": "alarm"
}
```

`command` 字段枚举：

- `alarm`：报警
- `shot`：拍照
- `video`：录像
- `video:off`: 关闭录像
- `update`：拉取配置
- `interphone:on`: 对讲机开启
- `interphone:off`：对讲机关闭
- `interphone:shot`：对讲机模式拍照
- `interphone:video`：对讲机模式录像
- `interphone:video:off`：对讲机模式关闭录像
- `mode:switch`: 模式切换

## 上行报警

包头：`[0x55, 0xad]`

包体：

```json
{
  "lng": "30",
  "lat": "110",
  "user_id": 1,
  "tenant_id": 1,
  "type": "alarm:sos",
  "timestamp": 11111111111,
  "detail": {
    "battery": 10,
    "field": 100
  }
}
```

字段解释：

```
lng: 经度
lat: 纬度
user_id: 用户 ID
tenant_id: 租户 ID
type: 报警类型(alarm:sos, alarm:battery, alarm:unwear, alarm:field, alarm:fence, alarm:fall)
    
timestamp: 时间戳
```
