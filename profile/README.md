# VistaCast · 视界云遥

**AI Visual Autopilot** — 软件 AI 摄像头云监控。  
Software that turns existing ONVIF/RTSP cameras into structured security and operations events.

VistaCast（视界云遥）接现场已经在用的工程摄像头。海康、大华、宇视、TP-Link VIGI 等支持 **ONVIF / RTSP** 的枪机与球机接入后，边缘完成检测，管理台和通知渠道收到结构化的安防与运营事件。

面向门店、仓储、工厂的运营方和集成商，以及居家看护与摄像头品牌合作。消费级摄像头 App 里的私有云机不在范围内。

## 一个平台，两条产品线

两条线共用账号、摄像头、规则和告警，不拆成两套系统。

### Enterprise · 门店 / 仓储 / 工厂

ToB 主线。买家是连锁运营、安保、工厂安全与系统集成商。

- 客流、区域入侵、摄像头离线告警
- Docker 私有化部署，数据可留在客户环境
- 按需预览：信令在云，媒体尽量点对点

### Guardian / OEM · 嵌入式与居家看护

第二条产品线。面向摄像头品牌与 ODM，以及家属和居家看护运营商。

- OEM 接入检测与事件能力，合作不必从一款商店 App 开始
- 家庭侧对跌倒和异常活动做联系人级联，由人确认后再继续传递
- 与 Enterprise 共用同一平台和同一套边缘运行时

看护交付的是事件和通知。平台不承诺 24 小时值班，也不自动拨打 120。

## 场景包

场景包是同一平台上的并行配置：按现场组合检测类型、区域规则和通知。开通一种场景，不必再买一个产品。

| 场景 | 覆盖 |
| :--- | :--- |
| 门店 | 客流（进店 / 过线）与区域入侵 |
| 仓储 | 摄像头离线，以及夜间、周界一类安防事件 |
| 工厂 | 危险区与异常行为；跌倒、烟雾等类型随告警质量扩展 |
| 居家看护 | 跌倒与异常活动的事件契约和场景包；通知到人，由人决定下一步 |
| PCB / 产线光学 | 实验室场景包：缺件、连锡、冷焊、虚焊等工位检测。与门店同一平台，不是独立产品，未对外发售 |

同一租户可以同时有零售站点和产线工位，共享权限与告警通道，按站点切换场景。

## 运行方式

接入摄像头 → 门店盒子或工位主机上的 AI 运行时 → 结构化事件 → 管理台与通知。

预览单独走一条路。云端交换信令；画面优先在观看端和现场之间点对点传输，直连失败再经 TURN 中继。没有人在看时，不把全帧率视频长期送上公网。

默认部署在客户自己的 Docker 环境。检测跑在边缘或客户主机上，不把自建云端 GPU 当作默认架构。需要补充识别时，可以编排第三方云视觉。

[VistaRemote](https://github.com/VistaRemote) 是并列产品：VistaCast 处理固定摄像头的视觉事件，VistaRemote 处理远程桌面。组织、代码和会话分开。

## 里程碑

平台按阶段交付。对外只讲已经能演示的能力。

- **M1 Horizon** — 接入、客流 / 入侵 / 离线、规则告警、私有化部署与按需预览
- **M2 Sentinel** — 告警质量、工厂异常类型、更多通知渠道
- **M3 Embedded + Guardian** — OEM 能力、家庭级联、门店盒子与端侧壳；这段栈可以在演示环境跑通
- **M4 Nexus** — 与 DataLuminary 等生态的衔接进行中，跨镜 Re-ID 为 β
- **M5 Module** — 定制摄像头模组按合作需求推进，尚未量产

可演示，未承诺已售。当前没有面向门店的生产发行标签，没有已售的云识别套餐，也不提供平台级 24/7 值班。门店盒子在通电且网络正常时可以持续检测，那是现场自运维。

## 入口

- 官网：[vistacast.dev](https://vistacast.dev)
- 文档：[docs.vistacast.dev](https://docs.vistacast.dev)
- 下载：[vistacast.dev/download](https://vistacast.dev/download)

公开仓库：

- [website](https://github.com/VistaCast/website) — 营销官网
- [docs](https://github.com/VistaCast/docs) — 文档源码，发布到 docs.vistacast.dev
- [downloads](https://github.com/VistaCast/downloads) — 公开安装包

Meta 仓以及 server、web、ai 等实现仓库为私有，不在本页展开。集成与合作从官网和文档开始。

## 启明工坊

VistaCast 是 [启明工坊 LuminaryWorks](https://luminaryworks.dev) 里负责空间视觉的产品：把现场摄像头变成可编排的事件。同一生态中，[DataLuminary](https://dataluminary.dev) 做数据洞察，[VistaRemote](https://github.com/VistaRemote) 做远程桌面，[SyncroBrain](https://syncrobrain.com)、[DoerFlow](https://doerflow.dev) 与 [BlockyEdu](https://blockyedu.com) 分别覆盖物联、任务与教育。视觉事件留在 VistaCast；分析、远程介入和后续业务走各自的产品。
