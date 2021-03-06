---

copyright:
  years:  2019
lastupdated: "2018-05-15"

keywords: number servers managed pool, managed pool

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 指定客户管理的池中的服务器数
{: #set-amount-servers-pool}

通过使用以下 API 调用来设置受管池中的服务器数：

|API 调用|参数|描述|
|---|---|---|
|<a href="https://softlayer.github.io/reference/services/SoftLayer_Account/setManagedPoolQuantity/" target="_blank">设置受管池数量</a>|poolKeyName|用于标识池的键名。IBM 会向您提供此值。|
|  |backendRouter|标识池的后端路由器。IBM 会向您提供此值。|
|  |quantity|您希望池中具有的服务器总数。<br><br>如果池中的当前服务器数量小于您在此处提供的值，那么将添加服务器。<br>如果池中的当前服务器数量大于您在此处提供的值，那么将除去服务器。|
