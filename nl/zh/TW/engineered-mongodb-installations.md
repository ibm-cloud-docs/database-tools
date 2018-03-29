---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 工程 MongoDB 的新增功能 <!--installations-->

已進行下列變更，來加強工程 {{site.data.keyword.mongodb}} 安裝的效能。這些變更使用 10gen 來提供工程伺服器的最佳可能使用者經驗。10gen 及 {{site.data.keyword.cloud}} 使用各種 {{site.data.keyword.baremetal_short}} 來作為平台基礎。<!--{{site.data.keyword.baremetal_short}} provide a consistent high performance set of available resources that cannot be matched in shared resource, multi-tenant platforms.-->  

* **CentOS 6.X 作為偏好的 OS** – 10gen 指出它們找到 CentOS 作業系統上支援 {{site.data.keyword.mongodb}} 的最佳效能及能力。基於此建議，{{site.data.keyword.cloud_notm}} 會專門將 {{site.data.keyword.mongodb}} 部署至 CentOS 6.X 平台。

* **設為 16 個區塊的 SSD 先讀預設值** - SSD 磁碟機有絕佳的探查時間，因此「先讀」可以設為 16 個區塊。旋轉磁碟可能需要少量緩衝，因此旋轉磁碟設為 32 個區塊。

* **Noatime** - 新增 noatime 讓系統不需要寫入至要讀取之檔案的檔案系統，這表示檔案存取速度會較快，且磁碟磨損會較少。

* **在 BIOS 中關閉 NUMA** - Linux、NUMA 及 {{site.data.keyword.mongodb}} 傾向不要一起運作。如果您在 NUMA 硬體上執行 {{site.data.keyword.mongodb}}，請將它關閉（使用交錯記憶體原則執行）。問題可能會以奇怪的方式出現，例如一段時間的明顯變慢或是高系統 CPU 時間。

* **ulimit** - 已開啟檔案的 ulimit 設為 64,000，而使用者處理程序的 ulimit 則設為 32,000。這些限制可防止因遺失可用檔案控點或使用者處理程序所造成的失敗。

* **EXT4** - 優先選取 Ext4，而非 Ext3。在配置檔案（或移除它們）時，ext3 可能太慢，而且大型檔案內的存取也不佳。

* **不同的日誌登載磁區** - 在 10gen 的建議下，{{site.data.keyword.cloud_notm}} 會使用針對日誌登載所裝載的不同 SSD 磁區。這可以在較高端工程伺服器上使用，並防止日誌登載干擾資料裝載的讀寫作業。

* **已預先安裝 MMS** - MMS 是免費提供給所有 {{site.data.keyword.mongodb}} 實例使用的 10gen 監視服務。所有 {{site.data.keyword.cloud_notm}} 工程伺服器都會預先配置 MMS 代理程式。
