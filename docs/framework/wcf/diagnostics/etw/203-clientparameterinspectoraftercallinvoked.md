---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1173aaa4bf01b324c8cd6088cd5646bc67f08c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="69999-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="69999-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="69999-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="69999-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69999-104">ID</span><span class="sxs-lookup"><span data-stu-id="69999-104">ID</span></span>|<span data-ttu-id="69999-105">203</span><span class="sxs-lookup"><span data-stu-id="69999-105">203</span></span>|  
|<span data-ttu-id="69999-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="69999-106">Keywords</span></span>|<span data-ttu-id="69999-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="69999-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="69999-108">レベル</span><span class="sxs-lookup"><span data-stu-id="69999-108">Level</span></span>|<span data-ttu-id="69999-109">情報</span><span class="sxs-lookup"><span data-stu-id="69999-109">Information</span></span>|  
|<span data-ttu-id="69999-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="69999-110">Channel</span></span>|<span data-ttu-id="69999-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="69999-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="69999-112">説明</span><span class="sxs-lookup"><span data-stu-id="69999-112">Description</span></span>  
 <span data-ttu-id="69999-113">このイベントは、クライアント パラメーター インスペクターで Service Model が `AfterCall` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="69999-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="69999-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="69999-114">Message</span></span>  
 <span data-ttu-id="69999-115">ディスパッチャーが型 '%1' の ClientParameterInspector で 'AfterCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="69999-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="69999-116">詳細</span><span class="sxs-lookup"><span data-stu-id="69999-116">Details</span></span>  
  
|<span data-ttu-id="69999-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="69999-117">Data Item Name</span></span>|<span data-ttu-id="69999-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="69999-118">Data Item Type</span></span>|<span data-ttu-id="69999-119">説明</span><span class="sxs-lookup"><span data-stu-id="69999-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="69999-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="69999-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="69999-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="69999-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="69999-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="69999-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="69999-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="69999-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="69999-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="69999-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="69999-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="69999-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="69999-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="69999-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="69999-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="69999-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
