---
layout: post
author: Vulkey_Chen
title: "我眼中的蓝队"
date: 2020-01-08
music-id: 
permalink: /archives/2020-01-08/1
description: "我眼中的蓝队"
---

# 我眼中的蓝队

仅聊一聊我自己眼中的蓝队，如有异议请指教。

作者：key

## 关于蓝队

蓝队：通常指攻防演习中的防守方

## 蓝队结构及服务

蓝队的结构比较复杂，参考：`https://shs3.b.qianxin.com/qax/24ebd5572b81ad98e97382851b861fb1.pdf`

本节所描述的“蓝队结构”仅仅来自个人的“第三方安全厂商”视角。

“第三方安全厂商”视角下的蓝队结构：队长、策略师、监察师

结构中的成员组成所对应的责任和技能如下：

队长：万变不离其宗，综合能力要强，但不一定需要精；擅长与客户沟通交流；熟悉了解攻防演习规则，划分人员对应工作；

策略师：熟悉了解安全厂商设备，并能根据实际情况进行策略调整和优化，以便阻挡常规类攻击；

监察师：熟悉了解安全厂商设备；熟悉并掌握渗透测试、应急响应等攻防能力；主要是分析和监控安全设备（监测类设备）的流量，分析告警信息、验证告警真实性；在演习规则允许的情况下可以进行一定的反制行为。

### 蓝队服务

攻防演习类项目、活动中经常会有厂商需要蓝队服务，因为大部分厂商：缺人、不具备攻防能力、不具备经验。

所以就诞生出了这么一个蓝队服务的“防守类”项目：主要在客户现场做技术支撑（分析和监控日志、验证告警信息、封堵IP...），大多数的时候，蓝队服务可能就只有1-2人，这时候会配合其他第三方人员进行防守任务。

## 蓝队建设

蓝队不能算是一种“常规化”的队伍，因为在大部分厂商内，负责防御体系的大多是运维人员，运维人员无法掌握较为“全面”的攻防能力。

在蓝队的建设这一块可以着重考虑内部转换、人才培养；由安全部门或第三方厂商人员组织培训。

一个真正具备“攻防能力”的人，都可以成为蓝队建设的一份子，也可以说渗透测试工程师有无限的其他转换可能，可塑性极强。

## 准备工作

1. 自检：攻防演习开始前应该进行内部的自我安全性检查、下架“历史残留”类“过期”业务、第三方服务泄露检查...
2. 设备：应具备常规的安全防护设备：WAF、流量监测、防火墙...
3. 摸排：时间充足的情况下可以邀请第三方安全厂商、安全部提前进行一遍“内部攻防演习”...
4. 分配：提前安排防守计划，购买蓝队服务...
5. 规则：提取蓝队得分项，准备“反制”等“得分措施”...