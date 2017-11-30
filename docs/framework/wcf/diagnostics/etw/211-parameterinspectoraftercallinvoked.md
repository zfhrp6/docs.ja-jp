---
title: 211 - ParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a66941a9b505267e976620bed238b02440968f14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="b5857-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="b5857-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b5857-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b5857-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5857-104">ID</span><span class="sxs-lookup"><span data-stu-id="b5857-104">ID</span></span>|<span data-ttu-id="b5857-105">211</span><span class="sxs-lookup"><span data-stu-id="b5857-105">211</span></span>|  
|<span data-ttu-id="b5857-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b5857-106">Keywords</span></span>|<span data-ttu-id="b5857-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b5857-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b5857-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b5857-108">Level</span></span>|<span data-ttu-id="b5857-109">情報</span><span class="sxs-lookup"><span data-stu-id="b5857-109">Information</span></span>|  
|<span data-ttu-id="b5857-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b5857-110">Channel</span></span>|<span data-ttu-id="b5857-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b5857-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5857-112">説明</span><span class="sxs-lookup"><span data-stu-id="b5857-112">Description</span></span>  
 <span data-ttu-id="b5857-113">このイベントは、Service Model が `AfterCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="b5857-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b5857-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b5857-114">Message</span></span>  
 <span data-ttu-id="b5857-115">ディスパッチャーが型 '%1' の ParameterInspector で 'AfterCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="b5857-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b5857-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b5857-116">Details</span></span>  
  
|<span data-ttu-id="b5857-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b5857-117">Data Item Name</span></span>|<span data-ttu-id="b5857-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b5857-118">Data Item Type</span></span>|<span data-ttu-id="b5857-119">説明</span><span class="sxs-lookup"><span data-stu-id="b5857-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b5857-120">型の名前</span><span class="sxs-lookup"><span data-stu-id="b5857-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="b5857-121">呼び出された `ParameterInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="b5857-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="b5857-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b5857-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b5857-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="b5857-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b5857-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="b5857-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b5857-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="b5857-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b5857-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b5857-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b5857-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b5857-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
