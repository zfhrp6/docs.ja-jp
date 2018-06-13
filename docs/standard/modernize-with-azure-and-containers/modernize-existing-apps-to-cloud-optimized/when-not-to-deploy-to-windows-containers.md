---
title: Windows コンテナーを展開しない場合
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |Windows コンテナーを展開しない場合
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 819f32955ff019414bef8820d17d272eddc11bf8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957962"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows コンテナーを展開しない場合

一部の Windows テクノロジは、Windows コンテナーによってサポートされていません。 ような場合、引き続き、通常は、Windows と IIS だけと共に、標準の Vm に移行する必要があります。

ケースが 2018年時点での Windows コンテナーでサポートされていません。 

-   現在 Microsoft メッセージ キュー (MSMQ) は他の以前のリリースではなく Windows Server v1803 リリースでは、に基づいて Windows コンテナーで使用可能なではのみです。 

    -   [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [ディスカッション フォーラム](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft 分散トランザクション コーディネーター (MSDTC) は、現在、Windows のコンテナーではサポートされません。

    -   [GitHub の問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   現在、Microsoft Office では、コンテナーはサポートしません。

    -   [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   UI アプリ (クライアント visual ユーザー インターフェイスを持つ) はサポートされているシナリオではありません。

-   Windows インフラストラクチャの役割 (DNS、DHCP、DC、NTP、印刷、ファイル サーバー、IAM など) がサポートされるシナリオではありません。


その他のサポートされないシナリオと、コミュニティからの要求は、Windows コンテナーの UserVoice フォーラムを参照してください:<https://windowsserver.uservoice.com/forums/304624-containers>です。

### <a name="additional-resources"></a>その他の技術情報

-   **仮想マシンと Azure 内のコンテナー**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[前へ](deploy-existing-net-apps-as-windows-containers.md)
[次へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
