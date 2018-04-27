---
title: Windows コンテナーを展開しない場合
description: コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Windows コンテナーを展開しない場合
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b8fb31a17d1f9d91fe053596685b7560a7fa1ee1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows コンテナーを展開しない場合

一部の Windows テクノロジは、Windows コンテナーによってサポートされていません。 ような場合、引き続き、通常は、Windows と IIS だけと共に、標準の Vm に移行する必要があります。

ケース 2017 中旬時点で Windows コンテナーでサポートされていません。

-   Microsoft メッセージ キュー (MSMQ) は、現在、Windows のコンテナーではサポートされません。

    -   [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [ディスカッション フォーラム](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft 分散トランザクション コーディネーター (MSDTC) が Windows コンテナーでサポートされていない現在

    -   [GitHub の問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office 現在サポートしていないコンテナー

    -   [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

その他のサポートされないシナリオと、コミュニティからの要求は、Windows コンテナーの UserVoice フォーラムを参照してください:<https://windowsserver.uservoice.com/forums/304624-containers>です。

### <a name="additional-resources"></a>その他の技術情報

-   **仮想マシンと Azure 内のコンテナー**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[前へ](deploy-existing-net-apps-as-windows-containers.md)
[次へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
