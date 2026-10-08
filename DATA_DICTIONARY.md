# 字段说明

## 扩展订单

| 字段 | 含义 | 单位或取值 |
|---|---|---|
| orderId | 实例内订单编号 | 唯一整数 |
| longitude、latitude | 经度、纬度 | 度 |
| x、y | 项目局部平面坐标 | km |
| customerType | 可用配送方式 | 1仅卡车；2仅无人机；3车机均可 |
| level | 服务等级 | 1、2、3 |
| demand | 需求重量 | kg |
| arrivalTime | 订单揭示时刻 | min |
| deadline | 服务评价截止时刻 | min |
| hardEarly、hardLate | 硬服务时间窗 | min |

时间从运营开始计，平面坐标未以配送中心重新归零。软时间窗缓冲参数见 `scenario_parameters.json`；扩展CSV未另列软时间窗。

## 主算例附加字段

`id`为订单编号；`name`、`district`和`zoneType`分别为地点、行政区及区域类型。`originalDemand`、`originalDeadline`为调整前属性；`demandAdjustmentReason`、`deadlineAdjustmentReason`和`classificationReason`说明调整或分类原因。`depotDistanceKm`为配送中心距离，`noFlyInfluence`为禁飞影响说明。其余文字字段及 `coreSet` 标记保留原文件值。

## 禁飞区域

`zoneId`为区域编号，`name`为场景名称，`longitude/latitude`及`x/y`为圆心位置，`radiusKm`为半径，`reason`为设定说明。这些区域用于仿真，不是官方空域边界。

## 场景索引

`poolSeed`为订单池生成种子，`solveSeed`为对应求解种子。

`nominalTrucks`和`nominalDronesPerTruck`为原车辆数及每车无人机数；`finalTrucks`和`finalDronesPerTruck`为离线增配测试的最终配置，规模实例中的最终配置栏留空。

`addedTrucks`为增加车辆数；`addedDrones`为车队无人机总数的增量，包括新增车辆搭载的无人机。

