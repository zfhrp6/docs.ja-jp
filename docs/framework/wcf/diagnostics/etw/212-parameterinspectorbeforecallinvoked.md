---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c428c9057e1538cfadb2b02bd05e2d61b4566399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="2d466-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="2d466-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="2d466-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2d466-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d466-104">ID</span><span class="sxs-lookup"><span data-stu-id="2d466-104">ID</span></span>|<span data-ttu-id="2d466-105">212</span><span class="sxs-lookup"><span data-stu-id="2d466-105">212</span></span>|  
|<span data-ttu-id="2d466-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2d466-106">Keywords</span></span>|<span data-ttu-id="2d466-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2d466-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2d466-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2d466-108">Level</span></span>|<span data-ttu-id="2d466-109">情報</span><span class="sxs-lookup"><span data-stu-id="2d466-109">Information</span></span>|  
|<span data-ttu-id="2d466-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2d466-110">Channel</span></span>|<span data-ttu-id="2d466-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2d466-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d466-112">説明</span><span class="sxs-lookup"><span data-stu-id="2d466-112">Description</span></span>  
 <span data-ttu-id="2d466-113">このイベントは、Service Model が `BeforeCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2d466-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d466-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2d466-114">Message</span></span>  
 <span data-ttu-id="2d466-115">ディスパッチャーが型 '%1' の ParameterInspector で 'BeforeCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="2d466-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d466-116">説明</span><span class="sxs-lookup"><span data-stu-id="2d466-116">Details</span></span>  
  
|<span data-ttu-id="2d466-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2d466-117">Data Item Name</span></span>|<span data-ttu-id="2d466-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2d466-118">Data Item Type</span></span>|<span data-ttu-id="2d466-119">説明</span><span class="sxs-lookup"><span data-stu-id="2d466-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d466-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="2d466-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="2d466-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="2d466-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="2d466-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="2d466-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="2d466-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="2d466-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2d466-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="2d466-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2d466-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="2d466-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2d466-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d466-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2d466-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2d466-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
