---
title: ".NET Framework のシステム要件"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b08bd7b78a8606f61c266da51f4079f0b5f4aac6
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2017
---
# <a name="net-framework-system-requirements"></a>.NET Framework のシステム要件

このトピックの表では、ハードウェア、オペレーティング システム、および .NET Framework 4.5 とそのポイント リリース (4.5.1 と 4.5.2)、ソフトウェアの要件を提供、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]とそのポイント リリース (4.6.1 および 4.6.2) と .NET Framework 4.7 とそのポイントリリース (4.7.1)。 .NET Framework 用のアプリケーションを開発するための開発環境では、要件セットが異なります。

ダウンロード情報とリンクについては、[「開発者向けの .NET Framework のインストール」](../../../docs/framework/install/guide-for-developers.md) を参照してください。

.NET Framework バージョンのサポート ライフサイクルについては、[マイクロソフト サポート ライフサイクル](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO)をご覧ください。

## <a name="hardware-requirements"></a>ハードウェア要件

|                          |        |
| ------------------------ | ------ |
| **プロセッサ**            | 1 GHz  |
| **RAM**                  | 512 MB |
| **ディスク容量 (最小)** |        |
| 32 ビット                   | 4.5 GB |
| 64 ビット                   | 4.5 GB |

## <a name="installation-requirements"></a>インストール要件

.NET Framework をインストールするには管理者権限が必要です。 .NET Framework をインストールするコンピューター上での管理者権限がない場合には、ネットワーク管理者にお問い合わせください。

## <a name="supported-client-operating-systems"></a>サポートされているクライアント オペレーティング システム

| オペレーティング システム | サポートされているエディション | OS と共にプレインストール済み | 個別にインストール可能 |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows 10 に収まる作成者を更新します。 | 32 ビットおよび 64 ビット | .NET framework 4.7.1 | |
| Windows 10 Creators Update | 32 ビットおよび 64 ビット | .NET Framework 4.7 | .Net framework 4.7.1 | 
| Windows 10 Anniversary Update | 32 ビットおよび 64 ビット | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows 10 の 11 月更新版 | 32 ビットおよび 64 ビット | [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] | |
| Windows 10 | 32 ビットおよび 64 ビット | [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] | [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32 ビット、64 ビット、および ARM | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32 ビット、64 ビット、および ARM | [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| Windows 7 SP1|32 ビットおよび 64 ビット | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1|
| Windows Vista SP2|32 ビットおよび 64 ビット | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |
| Windows XP |32 ビットおよび 64 ビット | -- | .NET Framework 4 |

 **注:**

- Windows 7 システムでは、.NET Framework には Windows 7 SP1 が必要です。 Windows 7 を使用していて Service Pack 1 をインストールしていない場合、.NET Framework をインストールする前に、Service Pack 1 をインストールする必要があります。

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は、Windows プレインストール環境 (Windows PE) でサポートされます。 Windows PE では、すべての機能がサポートされているわけではありません。

- .NET Framework 4 は、IA64 プラットフォームもサポートしています。

- すべてのプラットフォームについて最大限の互換性とセキュリティが得られるように、[Windows Update Web サイト](http://go.microsoft.com/fwlink/?LinkId=168461)から入手できる最新の Windows Service Pack にアップグレードし、重要な更新プログラムをインストールすることをお勧めします。

- 64 ビット オペレーティング システムでは、.NET Framework は WOW64 (64 ビット コンピューター上での 32 ビット処理) とネイティブ 64 ビット処理の両方をサポートしています。

## <a name="supported-server-operating-systems"></a>サポートされているサーバー オペレーティング システム

| オペレーティング システム | サポートされているエディション | OS と共にプレインストール済み | 個別にインストール可能 |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows サーバーのバージョン 1709 | 64 ビット | .NET framework 4.7.1 | -- |
| Windows Server 2016 | 64 ビット | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] | .NET Framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 R2 | 64 ビット | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 (64 ビット エディション) | 64 ビット| [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 R2 SP1|64 ビット | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 SP2|32 ビットおよび 64 ビット | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |

 **注:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] には [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] が含まれているため、個別にインストールする必要はありません。 同様に、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] には [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] が含まれます。

- .NET Framework には、Windows Server 2008 R2 sp1 以降の Server Core ロールのサポートが制限されています。 参照してください[サーバー コア .NET 機能](https://msdn.microsoft.com/library/ee391632.aspx)サポートされていない Api の一覧についてはします。

- .NET Framework は、itanium ベース システム用の Windows Server 2008 R2 でサポートされていません。

- Windows Server 2008 SP2 では、.NET Framework は、Server Core ロールでサポートされていません。

- すべてのプラットフォームについて最大限の互換性とセキュリティが得られるように、[Windows Update Web サイト](http://go.microsoft.com/fwlink/?LinkId=168461)から入手できる最新の Windows Service Pack にアップグレードし、重要な更新プログラムを適用することをお勧めします。 一部のオペレーティング システムでは、最新の Windows Service Pack のインストールが必要になる場合があります。

- 64 ビット オペレーティング システムでは、.NET Framework は WOW64 (64 ビット コンピューター上での 32 ビット処理) とネイティブ 64 ビット処理の両方をサポートしています。

## <a name="see-also"></a>関連項目

[インストール ガイド](../../../docs/framework/install/index.md)   
[はじめに](../../../docs/framework/get-started/index.md)   
[.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
