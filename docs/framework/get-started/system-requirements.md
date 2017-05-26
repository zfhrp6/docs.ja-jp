---
title: ".NET Framework のシステム要件 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
caps.latest.revision: 95
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: ddcefb2b35f8cbf06a3abcc16158eee850f799ff
ms.openlocfilehash: ec4594343c5a78649d7d7a4d151545612da9138b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/11/2017

---
# <a name="net-framework-system-requirements"></a>.NET Framework のシステム要件
このトピックの表では、.NET Framework 4.5 とそのポイント リリース (4.5.1 と 4.5.2)、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] とそのポイント リリース (4.6.1 と 4.6.2)、.NET Framework 4.7 のハードウェア、オペレーティング システム、およびソフトウェアの要件を示します。 .NET Framework 用のアプリケーションを開発するための開発環境では、要件セットが異なります。

 ダウンロード情報とリンクについては、[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)を参照してください。

 .NET Framework バージョンのサポート ライフサイクルについては、[マイクロソフト サポート ライフサイクル](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO)をご覧ください。

## <a name="hardware-requirements"></a>ハードウェア要件

|||
|-|-|
|**プロセッサ**|1 GHz|
|**RAM**|512 MB|
|**ディスク容量 (最小)**||
|32 ビット|4.5 GB|
|64 ビット|4.5 GB|

## <a name="installation-requirements"></a>インストール要件

- .NET Framework をインストールするには管理者権限が必要です。 .NET Framework をインストールするコンピューター上での管理者権限がない場合には、ネットワーク管理者にお問い合わせください。

## <a name="supported-client-operating-systems"></a>サポートされているクライアント オペレーティング システム

|オペレーティング システム|サポートされているエディション|OS と共にプレインストール済み|個別にインストール可能|
|----------------------|------------------------|------------------------------|----------------------------|
| Windows 10 Creators Update|32 ビットおよび 64 ビット|.NET Framework 4.7|| 
|Windows 10 Anniversary Update|32 ビットおよび 64 ビット|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|.NET Framework 4.7|
|Windows 10 の 11 月更新版|32 ビットおよび 64 ビット|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]||
|Windows 10|32 ビットおよび 64 ビット|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
|[!INCLUDE[win81](../../../includes/win81-md.md)]|32 ビット、64 ビット、および ARM|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]|[!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7|
|[!INCLUDE[win8](../../../includes/win8-md.md)]|32 ビット、64 ビット、および ARM|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
|Windows 7 SP1|32 ビットおよび 64 ビット|--|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|
|Windows Vista SP2|32 ビットおよび 64 ビット|--|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
|Windows XP|32 ビットおよび 64 ビット|--|.NET Framework 4|

 **注:**

- Windows 7 システムでは、.NET Framework には Windows 7 SP1 が必要です。 Windows 7 を使用していて Service Pack 1 をインストールしていない場合、.NET Framework をインストールする前に、Service Pack 1 をインストールする必要があります。

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は、Windows プレインストール環境 (Windows PE) でサポートされます。 Windows PE では、すべての機能がサポートされているわけではありません。

- .NET Framework 4 は、IA64 プラットフォームもサポートしています。

- すべてのプラットフォームについて最大限の互換性とセキュリティが得られるように、[Windows Update Web サイト](http://go.microsoft.com/fwlink/?LinkId=168461)から入手できる最新の Windows Service Pack にアップグレードし、重要な更新プログラムをインストールすることをお勧めします。

- 64 ビット オペレーティング システムでは、.NET Framework は WOW64 (64 ビット コンピューター上での 32 ビット処理) とネイティブ 64 ビット処理の両方をサポートしています。

## <a name="supported-server-operating-systems"></a>サポートされているサーバー オペレーティング システム

|オペレーティング システム|サポートされているエディション|OS と共にプレインストール済み|個別にインストール可能|
|----------------------|------------------------|------------------------------|----------------------------|
|Windows Server 2016|64 ビット|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|.NET Framework 4.7|
|[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]|64 ビット|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]|[!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7|
|[!INCLUDE[winserver8](../../../includes/winserver8-md.md)] (64 ビット エディション)|64 ビット|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7|
|Windows Server 2008 R2 SP1|64 ビット|--|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7|
|Windows Server 2008 SP2|32 ビットおよび 64 ビット|--|.NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|

 **注:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] には [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] が含まれているため、個別にインストールする必要はありません。 同様に、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] には [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] が含まれます。

- .NET Framework は、Windows Server 2008 R2 SP1 以降の Server Core ロールでサポートされていますが、Itanium ベース システム用の Windows Server 2008 R2 ではサポートされていません。

- Windows Server 2008 SP2 では、.NET Framework は、Server Core ロールでサポートされていません。

- すべてのプラットフォームについて最大限の互換性とセキュリティが得られるように、[Windows Update Web サイト](http://go.microsoft.com/fwlink/?LinkId=168461)から入手できる最新の Windows Service Pack にアップグレードし、重要な更新プログラムを適用することをお勧めします。 一部のオペレーティング システムでは、最新の Windows Service Pack のインストールが必要になる場合があります。

- 64 ビット オペレーティング システムでは、.NET Framework は WOW64 (64 ビット コンピューター上での 32 ビット処理) とネイティブ 64 ビット処理の両方をサポートしています。

## <a name="see-also"></a>関連項目
 [インストール ガイド](../../../docs/framework/install/guide-for-developers.md)   
 [はじめに](../../../docs/framework/get-started/index.md)   
 [トラブルシューティング](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
