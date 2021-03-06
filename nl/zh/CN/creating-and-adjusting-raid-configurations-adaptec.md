---

copyright:
  years: 2017, 2019
lastupdated: "2018-07-10"

keywords: raid, adaptec, ipmi, raid bios, raid array, RAID configuration

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 创建和调整 Adaptec RAID 配置
{: #bm-create-raid-config}

通过 Adaptec RAID BIOS，您可以配置和管理 RAID 设置。如果要使用[无操作系统](/docs/bare-metal?topic=bare-metal-the-no-os-option)选项，并且希望设置特定驱动器配置，请使用此 BIOS。

## 访问 IPMI 设备以与 RAID BIOS 交互
{: #bm-access-ipmi}

不管计算机是具有 Adaptec 控制器还是 LSI 控制器，您都需要访问使用 IPMI 的服务器，才能与 RAID BIOS 进行交互。为了与 IPMI 交互，您首先需要连接到 Adaptec {{site.data.keyword.cloud}} VPN。
1. 通过 [SSL](/docs/infrastructure/iaas-vpn?topic=VPN-setup-ssl-vpn-connections#setup-ssl-vpn-connections) 或 PPTP 登录到 VPN。
* 访问 [{{site.data.keyword.slportal}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/){: new_window} 中的“设备列表”。请参阅[访问设备列表](/docs/infrastructure/vsi?topic=virtual-servers-managing-virtual-servers)。
* 单击要访问的设备。
* 选择“远程管理”选项卡以查找服务器的 IPMI 访问详细信息。
* 向浏览器提交 IPMI 设备的 IP 并登录。
* 要开始与远程控制台交互，请单击**远程控制 > 控制台重定向**。

## 创建 RAID 阵列
{: #bm-create-raid-array}

在启动过程中，按 **Ctrl+A** 键以访问 RAID BIOS。

要开始配置 RAID，请打开“逻辑设备配置”（第一个选项）。此选项会扫描驱动器的拓扑并显示一个菜单，通过该菜单可管理阵列、创建阵列和完成其他驱动器管理任务。

以下示例显示如何创建阵列。这将向您显示可在创建 RAID 阵列时使用的可用驱动器的列表。

1. 要选择驱动器，请按空格键以填充*所选驱动器*框。
* 选择好要在阵列中使用的所有驱动器后，按 ENTER 键以转至 RAID 配置步骤。
* 选择要使用的 RAID 类型。如果您需要帮助来确定哪个 RAID 设置最适合您的需求，请参阅以下 [Adaptec 常见问题 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.adaptec.com/en-us/_common/compatibility/_education/raid_level_compar_wp.htm){: new_window}。
* 在配置过程中提供“阵列标签”。最好在标签中包含 RAID 类型（例如：RAID10-A）。
* 按 **Enter** 键以转至其余设置。请使用缺省值。

完成配置后，选择“完成”；这将创建 RAID。可以通过从主菜单中选择“管理阵列”来查看新阵列。要退出配置实用程序，请按 ESC 键，直至提示您退出 Adaptec BIOS。

## 除去现有 RAID 阵列
{: #bm-remove-raid-array}

如果需要除去现有阵列，请转至**管理阵列**，选择要除去的阵列，然后按**删除**并确认。

## 示例配置
{: #bm-example-config}

1. 在一台共有 6 个驱动器的服务器上，可以在 RAID 0 中设置 2 个 SSD 用于操作系统，在 RAID 10 中再设置 4 个驱动器用于实际数据。使用此配置可快速重装服务器的操作系统，而无需复原站点或服务数据（如果它位于辅助阵列上）。

* 在 cPanel 服务器上，可以使 /var 和 /home 位于单独的 SSD RAID 阵列上。由于目录是 cPanel 服务器上 IO 密集程度最高的两个目录，因此使用以下设置有可能缩短站点响应时间：
  * RAID0（2 个 SATA 驱动器）- /
  * RAID0（2 个 SSD 驱动器）- /var
  * RAID0（2 个 SSD 驱动器）- /home
  * RAID10（4 个 SATA 驱动器）- /backup

* 使用单个 RAID 阵列来设置多个逻辑分区。例如，使用在 RAID 1 中设置的 2 个 4 TB 驱动器。可对 RAID 进行分区以满足您的需求。请参阅以下示例：
  * 主分区 100 GB，用于操作系统
  * 第二个分区 500 GB，用于数据
  * 剩余空间作为第三个分区，用于备份
