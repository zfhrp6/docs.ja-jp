---
title: 209 - MessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9083a6dc9849fcd177b1e6a38ca7bb72e7799dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="21c5a-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="21c5a-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="21c5a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="21c5a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21c5a-104">ID</span><span class="sxs-lookup"><span data-stu-id="21c5a-104">ID</span></span>|<span data-ttu-id="21c5a-105">209</span><span class="sxs-lookup"><span data-stu-id="21c5a-105">209</span></span>|  
|<span data-ttu-id="21c5a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="21c5a-106">Keywords</span></span>|<span data-ttu-id="21c5a-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="21c5a-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="21c5a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="21c5a-108">Level</span></span>|<span data-ttu-id="21c5a-109">情報</span><span class="sxs-lookup"><span data-stu-id="21c5a-109">Information</span></span>|  
|<span data-ttu-id="21c5a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="21c5a-110">Channel</span></span>|<span data-ttu-id="21c5a-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="21c5a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21c5a-112">説明</span><span class="sxs-lookup"><span data-stu-id="21c5a-112">Description</span></span>  
 <span data-ttu-id="21c5a-113">このイベントは、メッセージ インスペクターで Service Model が `BeforeSend` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="21c5a-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21c5a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="21c5a-114">Message</span></span>  
 <span data-ttu-id="21c5a-115">ディスパッチャーが型 '%1' の MessageInspector で 'BeforeSendRequest' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="21c5a-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21c5a-116">説明</span><span class="sxs-lookup"><span data-stu-id="21c5a-116">Details</span></span>  
  
|<span data-ttu-id="21c5a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="21c5a-117">Data Item Name</span></span>|<span data-ttu-id="21c5a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="21c5a-118">Data Item Type</span></span>|<span data-ttu-id="21c5a-119">説明</span><span class="sxs-lookup"><span data-stu-id="21c5a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21c5a-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="21c5a-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="21c5a-121">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="21c5a-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="21c5a-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="21c5a-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="21c5a-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="21c5a-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="21c5a-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="21c5a-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="21c5a-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="21c5a-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="21c5a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21c5a-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="21c5a-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="21c5a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
