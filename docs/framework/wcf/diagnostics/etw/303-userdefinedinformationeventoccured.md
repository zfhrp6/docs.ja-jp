---
title: 303 - UserDefinedInformationEventOccured
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="ec5c5-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="ec5c5-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="ec5c5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ec5c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec5c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec5c5-104">ID</span></span>|<span data-ttu-id="ec5c5-105">303</span><span class="sxs-lookup"><span data-stu-id="ec5c5-105">303</span></span>|  
|<span data-ttu-id="ec5c5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ec5c5-106">Keywords</span></span>|<span data-ttu-id="ec5c5-107">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="ec5c5-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="ec5c5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ec5c5-108">Level</span></span>|<span data-ttu-id="ec5c5-109">情報</span><span class="sxs-lookup"><span data-stu-id="ec5c5-109">Information</span></span>|  
|<span data-ttu-id="ec5c5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ec5c5-110">Channel</span></span>|<span data-ttu-id="ec5c5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ec5c5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec5c5-112">説明</span><span class="sxs-lookup"><span data-stu-id="ec5c5-112">Description</span></span>  
 <span data-ttu-id="ec5c5-113">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-113">This event is emitted from user code.</span></span> <span data-ttu-id="ec5c5-114">開発者は、カスタム定義の情報イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="ec5c5-115">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="ec5c5-116">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec5c5-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ec5c5-117">Message</span></span>  
 <span data-ttu-id="ec5c5-118">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="ec5c5-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec5c5-119">詳細</span><span class="sxs-lookup"><span data-stu-id="ec5c5-119">Details</span></span>  
  
|<span data-ttu-id="ec5c5-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ec5c5-120">Data Item Name</span></span>|<span data-ttu-id="ec5c5-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ec5c5-121">Data Item Type</span></span>|<span data-ttu-id="ec5c5-122">説明</span><span class="sxs-lookup"><span data-stu-id="ec5c5-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec5c5-123">名前</span><span class="sxs-lookup"><span data-stu-id="ec5c5-123">Name</span></span>|`xs:string`|<span data-ttu-id="ec5c5-124">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="ec5c5-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="ec5c5-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="ec5c5-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ec5c5-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ec5c5-128">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ec5c5-129">Payload</span><span class="sxs-lookup"><span data-stu-id="ec5c5-129">Payload</span></span>|`xs:string`|<span data-ttu-id="ec5c5-130">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="ec5c5-130">The user-defined payload of the event.</span></span>|
