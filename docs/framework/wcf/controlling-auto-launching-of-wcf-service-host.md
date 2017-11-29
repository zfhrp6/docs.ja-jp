---
title: "WCF サービス ホストの自動起動の制御"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc89ed3ae41471af49fc92f31834f0ae268309dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="c795e-102">WCF サービス ホストの自動起動の制御</span><span class="sxs-lookup"><span data-stu-id="c795e-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="c795e-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] ソリューションに複数のプロジェクトが含まれている場合、既定では、同じソリューション内の別のプロジェクトをデバッグするときでも、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトの [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] サービス ホスト (WcfSvcHost.exe) が自動的に起動します。この自動起動機能は制御できます。</span><span class="sxs-lookup"><span data-stu-id="c795e-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="c795e-104">これを行うを右クリックし、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]でサービス プロジェクト**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリック**WCF オプション**タブです。**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに** チェック ボックスが既定で有効にします。</span><span class="sxs-lookup"><span data-stu-id="c795e-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="c795e-105">チェック ボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを起動しないように指定できます。</span><span class="sxs-lookup"><span data-stu-id="c795e-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="c795e-106">この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="c795e-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="c795e-107">このオプションは、次のプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c795e-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="c795e-108"> サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="c795e-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="c795e-109">シーケンシャル ワークフロー サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="c795e-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="c795e-110">ステート マシン ワークフロー サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="c795e-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="c795e-111">配信サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="c795e-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c795e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c795e-112">See Also</span></span>  
 [<span data-ttu-id="c795e-113">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="c795e-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
