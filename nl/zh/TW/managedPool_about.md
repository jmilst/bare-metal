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

# 關於客戶管理的儲存區
{: #bm-customer-managed-pools}

客戶管理的儲存區可讓您存取一律可供組織使用的一組伺服器。這些伺服器是針對您的規格配置。您可以在需要時從儲存區訂購伺服器。

此特性最適合您的組織經常需要佈建許多伺服器以便用於尖峰期間的情況。使用此特性，您可以只使用所需伺服器的數目下限，但隨時都有一大組可用伺服器，可以滿足您的額外需要。

## 使用範例
{: #bm-managed-pools-use-case}

公司 A 在每日作業中使用 1000 部作用中伺服器。不過，在尖峰時間，他們可能額外需要多達 500 部伺服器。他們需要額外的伺服器能快速啟動並執行。

為了符合他們的需求，公司 A 聯絡 IBM 以設定伺服器的受管理儲存區。設定儲存區之後，他們進行了 API 呼叫，將儲存區中的伺服器數目設為 500。

在七月，公司 A 需要從儲存區中額外使用 250 部伺服器。他們訂購了 250 部伺服器。這張訂單快速地以來自儲存區的 250 部伺服器履行。完成訂單之後，會將 250 部伺服器新增至公司 A 的受管理儲存區，以便他們隨時有 500 部可用。


## 後續步驟

如果您的組織想要使用客戶管理的儲存區，請參閱[佈建客戶管理的儲存區](/bare-metal?topic=bare-metal-provisioning-customer-managed-pools)。
