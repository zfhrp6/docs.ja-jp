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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc291469721915f399fe5acfa3200716939fee4c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="6697f-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="6697f-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="6697f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6697f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6697f-104">ID</span><span class="sxs-lookup"><span data-stu-id="6697f-104">ID</span></span>|<span data-ttu-id="6697f-105">303</span><span class="sxs-lookup"><span data-stu-id="6697f-105">303</span></span>|  
|<span data-ttu-id="6697f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6697f-106">Keywords</span></span>|<span data-ttu-id="6697f-107">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="6697f-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="6697f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6697f-108">Level</span></span>|<span data-ttu-id="6697f-109">情報</span><span class="sxs-lookup"><span data-stu-id="6697f-109">Information</span></span>|  
|<span data-ttu-id="6697f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6697f-110">Channel</span></span>|<span data-ttu-id="6697f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6697f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6697f-112">説明</span><span class="sxs-lookup"><span data-stu-id="6697f-112">Description</span></span>  
 <span data-ttu-id="6697f-113">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="6697f-113">This event is emitted from user code.</span></span> <span data-ttu-id="6697f-114">開発者は、カスタム定義の情報イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6697f-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="6697f-115">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="6697f-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="6697f-116">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="6697f-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6697f-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6697f-117">Message</span></span>  
 <span data-ttu-id="6697f-118">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="6697f-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="6697f-119">詳細</span><span class="sxs-lookup"><span data-stu-id="6697f-119">Details</span></span>  
  
|<span data-ttu-id="6697f-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6697f-120">Data Item Name</span></span>|<span data-ttu-id="6697f-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6697f-121">Data Item Type</span></span>|<span data-ttu-id="6697f-122">説明</span><span class="sxs-lookup"><span data-stu-id="6697f-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6697f-123">名前</span><span class="sxs-lookup"><span data-stu-id="6697f-123">Name</span></span>|`xs:string`|<span data-ttu-id="6697f-124">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="6697f-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="6697f-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="6697f-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="6697f-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="6697f-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6697f-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="6697f-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6697f-128">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="6697f-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6697f-129">Payload</span><span class="sxs-lookup"><span data-stu-id="6697f-129">Payload</span></span>|`xs:string`|<span data-ttu-id="6697f-130">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="6697f-130">The user-defined payload of the event.</span></span>|
