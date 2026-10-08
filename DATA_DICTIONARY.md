# 字段说明

## Java扩展订单CSV

| 字段 | 含义 | 单位 |
|---|---|---|
| orderId | 实例内唯一订单编号 | 无 |
| longitude / latitude | 经度 / 纬度 | 度 |
| x / y | 项目局部平面坐标；不是从配送中心重新归零的坐标 | km |
| customerType | 1仅卡车；2仅无人机；3车机均可 | 无 |
| level | 服务等级1、2、3，用于匹配优先级及时间窗设定 | 无 |
| demand | 需求重量 | kg |
| arrivalTime | 订单揭示时刻 | min |
| deadline | 服务评价的截止时刻 | min |
| hardEarly / hardLate | 硬服务时间窗起点 / 终点 | min |

扩展CSV只保留快照中已有输入字段，不增加推断的软时间窗。软时间窗缓冲参数保存在`scenario_parameters.json`，并需结合相应模型规则使用。空间扰动实例同时保留实际使用的坐标，禁止只取原始经纬度重新生成未扰动位置。

## 主算例CSV的补充字段

`id`对应订单编号，`name`与`district`为场景地点和行政区标签，`zoneType`为区域类型。`originalDemand`、`originalDeadline`为文件中保留的调整前属性；`demandAdjustmentReason`、`deadlineAdjustmentReason`、`classificationReason`记录调整及分类说明。`note`、`serviceClassName`为文字说明，`depotDistanceKm`为配送中心距离，`noFlyInfluence`为场景禁飞影响说明。`coreSet`为原文件标记，本包保留其原值，不赋予未核验的新含义。

## 禁飞区域CSV

`zoneId`为区域编号，`name`为场景名称，`longitude/latitude`及`x/y`为圆心位置，`radiusKm`为模拟圆形区域半径，`reason`为场景设定说明。

## scenario_index.csv

`poolSeed`为订单池生成种子，`solveSeed`仅为原运行的求解种子记录，不提供求解器。
`nominalTrucks`和`nominalDronesPerTruck`为原可用配置；`finalTrucks`和`finalDronesPerTruck`为最终离线测试配置，规模实例中该部分留空。
`addedTrucks`为增加车辆数；`addedDrones`为车队无人机总量增加数，不是每车增量。
