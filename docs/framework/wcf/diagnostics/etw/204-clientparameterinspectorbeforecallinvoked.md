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
ms.openlocfilehash: 2b30e53803692b7127d63a67b2c2c4178dc645db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="7c69f-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="7c69f-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="7c69f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7c69f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c69f-104">ID</span><span class="sxs-lookup"><span data-stu-id="7c69f-104">ID</span></span>|<span data-ttu-id="7c69f-105">204</span><span class="sxs-lookup"><span data-stu-id="7c69f-105">204</span></span>|  
|<span data-ttu-id="7c69f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7c69f-106">Keywords</span></span>|<span data-ttu-id="7c69f-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7c69f-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7c69f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7c69f-108">Level</span></span>|<span data-ttu-id="7c69f-109">情報</span><span class="sxs-lookup"><span data-stu-id="7c69f-109">Information</span></span>|  
|<span data-ttu-id="7c69f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7c69f-110">Channel</span></span>|<span data-ttu-id="7c69f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7c69f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7c69f-112">説明</span><span class="sxs-lookup"><span data-stu-id="7c69f-112">Description</span></span>  
 <span data-ttu-id="7c69f-113">このイベントは、クライアント パラメーター インスペクターで Service Model が `BeforeCall` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c69f-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7c69f-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7c69f-114">Message</span></span>  
 <span data-ttu-id="7c69f-115">ディスパッチャーが型 '%1' の ClientParameterInspector で 'BeforeCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="7c69f-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7c69f-116">詳細</span><span class="sxs-lookup"><span data-stu-id="7c69f-116">Details</span></span>  
  
|<span data-ttu-id="7c69f-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7c69f-117">Data Item Name</span></span>|<span data-ttu-id="7c69f-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7c69f-118">Data Item Type</span></span>|<span data-ttu-id="7c69f-119">説明</span><span class="sxs-lookup"><span data-stu-id="7c69f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7c69f-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="7c69f-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="7c69f-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="7c69f-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="7c69f-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="7c69f-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="7c69f-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="7c69f-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7c69f-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="7c69f-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7c69f-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="7c69f-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7c69f-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7c69f-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7c69f-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7c69f-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
