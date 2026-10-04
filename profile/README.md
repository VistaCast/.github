# VistaCast · 视界云遥

**场景智能 · 产线光学**  
Scene intelligence · Line optics

VistaCast（视界云遥）是工业与现场运营的视觉平台。现场已经在用的 ONVIF / RTSP 摄像头接入后，边缘完成检测，管理台和通知渠道收到结构化事件。它服务工程摄像头与产线工位，不包含消费级私有云摄像机，也不包含远程桌面。

## 产品方向

### 产线光学 / AOI

PCB / PCBA 及相邻工位是 VistaCast 的主要产品方向：缺件、错件与偏移，条码和标签是否在位，焊点缺陷（虚焊、连锡、冷焊），以及胶路与组装有无。实验室已在体量可观的数据集上完成本地训练与评估，包括公开的 PCB-AoI、映射后的 DeepPCB，以及内部夹具。推理跑在边缘或工位主机的 CPU 上（Apple Silicon，或 Intel / AMD PC），权重不进浏览器。这些结果不作为客户板 F1，AOI 也尚未作为独立 SKU 发售；配置、模型与告警仍在同一套 VistaCast 控制面上。

### 智能安防

覆盖区域入侵、周界、夜间活动和摄像头离线，面向零售门店、仓储和园区里已经装好的枪机与球机。人进入划定区域、夜间出现不该有的活动、设备掉线，都写成可路由的事件。值班人员在管理台和通知渠道里处理这些事件。

### 工业安全

面向工厂 EHS：危险区域占用，以及跌倒、烟雾一类可配置异常。规则按工位和区域配置，告警进入现有通知渠道，由现场人员确认和处理。检测类型随告警质量扩展；当前实验室阈值不是已认证的安全联锁。

### 商业零售运营

连锁门店用同一路摄像头看客流、高峰时段和区域关注。进店、过线与区域停留写成运营事件，供排班和陈列使用。零售规则按站点打开，与安防告警共用账号和摄像头。

### 仓储与园区

覆盖月台装卸、无人值守的夜间，以及园区周界枪机。装卸口占用、夜间不该出现的活动、周界进入，按站点配置成事件。摄像头离线同样告警，避免断流只在回放里才被发现。

### 居家看护与 OEM

跌倒和异常活动通知到指定的人，由人决定下一步。摄像头品牌与 ODM 可以按 OEM 能力接入检测和事件，合作不必从一款商店 App 开始。平台不自动拨打 120，也不承诺平台级 24 小时值班。

## 共用底座

账号、摄像头、场景配置、模型和告警在同一平台上编排。多开一个方向是改配置和模型，不必再装一套系统；零售站点与产线工位可以留在同一租户里，按站点切换。检测在边缘或客户主机完成。预览按需进行：云端交换信令，画面优先在观看端与现场之间点对点，直连失败再经 TURN。

## 交付形态

同一底座按买家分成两种交付。Enterprise 面向连锁运营、安保、工厂与系统集成商，以 Docker 私有化部署，数据可留在客户环境。Guardian / OEM 面向摄像头品牌、ODM 与居家看护运营商；家庭侧由人确认后再级联通知，与 Enterprise 共用平台和边缘运行时。

## 里程碑

平台按阶段交付，对外只讲已经能演示的能力。可演示不等于已售。

- **M1 Horizon** — 摄像头接入，客流、入侵与离线告警，规则与私有化部署，按需预览。本机实验室可跑，未打生产发行标签。
- **M2 Sentinel** — 告警质量、工厂异常类型和更多通知渠道。必须切片已关闭；客户真集上的准确率尚未作为验收结论。
- **M3 Embedded + Guardian** — OEM 能力、家庭级联、门店盒子与端侧壳。演示环境可跑通；未打生产标签，未上架商店。
- **M4 Nexus** — 与 DataLuminary 的模板衔接，跨镜 Re-ID 为 β。产线光学（M4.1）已在实验室对公开 PCB 缺陷集和内部夹具完成训练与评估，可在工位主机上跑通。
- **M5 Module** — 定制摄像头模组按合作推进，尚未量产。

当前没有面向门店的生产发行标签，也没有已售的云识别套餐。门店盒子在通电且网络正常时可以持续检测，那是现场自运维。

## 入口

- 官网：[vistacast.dev](https://vistacast.dev)
- 文档：[docs.vistacast.dev](https://docs.vistacast.dev)
- 下载：[vistacast.dev/download](https://vistacast.dev/download)

公开仓库：[website](https://github.com/VistaCast/website)（营销官网）、[docs](https://github.com/VistaCast/docs)（文档源码，发布到 docs.vistacast.dev）、[downloads](https://github.com/VistaCast/downloads)（公开安装包）。Meta 以及 server、web、ai 等实现仓库为私有。集成与合作从官网和文档开始。

VistaCast 属于 [启明工坊 LuminaryWorks](https://luminaryworks.dev)，负责把现场摄像头变成可编排的视觉事件。同一生态里，[DataLuminary](https://dataluminary.dev) 做数据洞察，[VistaRemote](https://github.com/VistaRemote) 做远程桌面，[SyncroBrain](https://syncrobrain.com)、[DoerFlow](https://doerflow.dev) 与 [BlockyEdu](https://blockyedu.com) 分别覆盖物联、任务与教育。
