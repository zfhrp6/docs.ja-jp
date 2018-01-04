---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d737a7334098961cccb73a114be9be5bb71727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="c17da-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="c17da-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="c17da-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c17da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c17da-104">ID</span><span class="sxs-lookup"><span data-stu-id="c17da-104">ID</span></span>|<span data-ttu-id="c17da-105">202</span><span class="sxs-lookup"><span data-stu-id="c17da-105">202</span></span>|  
|<span data-ttu-id="c17da-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c17da-106">Keywords</span></span>|<span data-ttu-id="c17da-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c17da-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c17da-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c17da-108">Level</span></span>|<span data-ttu-id="c17da-109">情報</span><span class="sxs-lookup"><span data-stu-id="c17da-109">Information</span></span>|  
|<span data-ttu-id="c17da-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c17da-110">Channel</span></span>|<span data-ttu-id="c17da-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c17da-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c17da-112">説明</span><span class="sxs-lookup"><span data-stu-id="c17da-112">Description</span></span>  
 <span data-ttu-id="c17da-113">このイベントは、クライアント メッセージ インスペクターで Service Model が `BeforeSendRequest` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="c17da-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c17da-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c17da-114">Message</span></span>  
 <span data-ttu-id="c17da-115">ディスパッチャーが型 '%1' の ClientMessageInspector で 'BeforeSendRequest' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="c17da-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c17da-116">説明</span><span class="sxs-lookup"><span data-stu-id="c17da-116">Details</span></span>  
  
|<span data-ttu-id="c17da-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c17da-117">Data Item Name</span></span>|<span data-ttu-id="c17da-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c17da-118">Data Item Type</span></span>|<span data-ttu-id="c17da-119">説明</span><span class="sxs-lookup"><span data-stu-id="c17da-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c17da-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="c17da-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="c17da-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="c17da-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="c17da-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="c17da-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="c17da-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="c17da-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c17da-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="c17da-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c17da-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="c17da-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c17da-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c17da-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c17da-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c17da-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
