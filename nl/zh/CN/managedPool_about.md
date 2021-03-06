---

copyright:
  years:  2019
lastupdated: "2018-05-15"

keywrods: bare metal, managed pools

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 关于客户管理的池
{: #bm-customer-managed-pools}

通过客户管理的池，您可以访问一组始终可供组织使用的服务器。这些服务器根据您的规范进行配置。您可以在需要时订购池中的服务器。

如果您的组织经常需要供应许多服务器以在高峰时段使用，那么此功能是理想的选择。使用此功能时，您可以只使用所需最少数量的服务器，但始终有一大组服务器可用于满足您的额外需求。

## 用途示例
{: #bm-managed-pools-use-case}

公司 A 的日常运营中使用了 1000 台活动服务器。但是，在高峰时间，可能额外需要 500 台服务器。公司 A 需要快速启动并运行这些额外的服务器。

为了满足自身需求，公司 A 联系 IBM 来设置受管的服务器池。设置池后，公司 A 发起 API 调用，以将池中的服务器数设置为 500。

在 7 月份，公司 A 额外需要其池中的 250 台服务器。为此，他们订购了 250 台服务器。此订单通过池中的 250 个服务器快速供货。订单完成后，将向公司 A 的受管池添加 250 台服务器，以便池中始终有 500 台服务器可用。


## 后续步骤

如果您的组织希望使用客户管理的池，请参阅[供应客户管理的池](/bare-metal?topic=bare-metal-provisioning-customer-managed-pools)。
