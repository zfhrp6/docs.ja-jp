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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="e2388-103">Windows コンテナーを展開しない場合</span><span class="sxs-lookup"><span data-stu-id="e2388-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="e2388-104">一部の Windows テクノロジは、Windows コンテナーによってサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e2388-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="e2388-105">ような場合、引き続き、通常は、Windows と IIS だけと共に、標準の Vm に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2388-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="e2388-106">ケース 2017 中旬時点で Windows コンテナーでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e2388-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="e2388-107">Microsoft メッセージ キュー (MSMQ) は、現在、Windows のコンテナーではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e2388-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="e2388-108">UserVoice 要求フォーラム</span><span class="sxs-lookup"><span data-stu-id="e2388-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="e2388-109">ディスカッション フォーラム</span><span class="sxs-lookup"><span data-stu-id="e2388-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="e2388-110">Microsoft 分散トランザクション コーディネーター (MSDTC) が Windows コンテナーでサポートされていない現在</span><span class="sxs-lookup"><span data-stu-id="e2388-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="e2388-111">GitHub の問題</span><span class="sxs-lookup"><span data-stu-id="e2388-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="e2388-112">Microsoft Office 現在サポートしていないコンテナー</span><span class="sxs-lookup"><span data-stu-id="e2388-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="e2388-113">UserVoice 要求フォーラム</span><span class="sxs-lookup"><span data-stu-id="e2388-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="e2388-114">その他のサポートされないシナリオと、コミュニティからの要求は、Windows コンテナーの UserVoice フォーラムを参照してください:<https://windowsserver.uservoice.com/forums/304624-containers>です。</span><span class="sxs-lookup"><span data-stu-id="e2388-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e2388-115">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="e2388-115">Additional resources</span></span>

-   <span data-ttu-id="e2388-116">**仮想マシンと Azure 内のコンテナー**</span><span class="sxs-lookup"><span data-stu-id="e2388-116">**Virtual machines and containers in Azure**</span></span>

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="e2388-117">[前へ](deploy-existing-net-apps-as-windows-containers.md)
[次へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="e2388-117">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
