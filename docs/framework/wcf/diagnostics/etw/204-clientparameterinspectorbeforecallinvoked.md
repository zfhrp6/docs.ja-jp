---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a25315a6008be69aeb534b8bf26c0e813c00c01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="91e35-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="91e35-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="91e35-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="91e35-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91e35-104">ID</span><span class="sxs-lookup"><span data-stu-id="91e35-104">ID</span></span>|<span data-ttu-id="91e35-105">204</span><span class="sxs-lookup"><span data-stu-id="91e35-105">204</span></span>|  
|<span data-ttu-id="91e35-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="91e35-106">Keywords</span></span>|<span data-ttu-id="91e35-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="91e35-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="91e35-108">レベル</span><span class="sxs-lookup"><span data-stu-id="91e35-108">Level</span></span>|<span data-ttu-id="91e35-109">情報</span><span class="sxs-lookup"><span data-stu-id="91e35-109">Information</span></span>|  
|<span data-ttu-id="91e35-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="91e35-110">Channel</span></span>|<span data-ttu-id="91e35-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="91e35-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91e35-112">説明</span><span class="sxs-lookup"><span data-stu-id="91e35-112">Description</span></span>  
 <span data-ttu-id="91e35-113">このイベントは、クライアント パラメーター インスペクターで Service Model が `BeforeCall` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="91e35-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91e35-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="91e35-114">Message</span></span>  
 <span data-ttu-id="91e35-115">ディスパッチャーが型 '%1' の ClientParameterInspector で 'BeforeCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="91e35-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91e35-116">説明</span><span class="sxs-lookup"><span data-stu-id="91e35-116">Details</span></span>  
  
|<span data-ttu-id="91e35-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="91e35-117">Data Item Name</span></span>|<span data-ttu-id="91e35-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="91e35-118">Data Item Type</span></span>|<span data-ttu-id="91e35-119">説明</span><span class="sxs-lookup"><span data-stu-id="91e35-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91e35-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="91e35-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="91e35-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="91e35-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="91e35-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="91e35-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="91e35-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="91e35-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="91e35-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="91e35-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="91e35-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="91e35-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="91e35-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91e35-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="91e35-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="91e35-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
