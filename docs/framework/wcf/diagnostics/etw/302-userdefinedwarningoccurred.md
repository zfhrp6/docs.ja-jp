---
title: 302 - UserDefinedWarningOccurred
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="9d6e5-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="9d6e5-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="9d6e5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9d6e5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d6e5-104">ID</span><span class="sxs-lookup"><span data-stu-id="9d6e5-104">ID</span></span>|<span data-ttu-id="9d6e5-105">302</span><span class="sxs-lookup"><span data-stu-id="9d6e5-105">302</span></span>|  
|<span data-ttu-id="9d6e5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="9d6e5-106">Keywords</span></span>|<span data-ttu-id="9d6e5-107">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="9d6e5-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="9d6e5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="9d6e5-108">Level</span></span>|<span data-ttu-id="9d6e5-109">警告</span><span class="sxs-lookup"><span data-stu-id="9d6e5-109">Warning</span></span>|  
|<span data-ttu-id="9d6e5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9d6e5-110">Channel</span></span>|<span data-ttu-id="9d6e5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9d6e5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d6e5-112">説明</span><span class="sxs-lookup"><span data-stu-id="9d6e5-112">Description</span></span>  
 <span data-ttu-id="9d6e5-113">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-113">This event is emitted from user code.</span></span> <span data-ttu-id="9d6e5-114">開発者は、カスタム定義の警告イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="9d6e5-115">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="9d6e5-116">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d6e5-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="9d6e5-117">Message</span></span>  
 <span data-ttu-id="9d6e5-118">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="9d6e5-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d6e5-119">説明</span><span class="sxs-lookup"><span data-stu-id="9d6e5-119">Details</span></span>  
  
|<span data-ttu-id="9d6e5-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9d6e5-120">Data Item Name</span></span>|<span data-ttu-id="9d6e5-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9d6e5-121">Data Item Type</span></span>|<span data-ttu-id="9d6e5-122">説明</span><span class="sxs-lookup"><span data-stu-id="9d6e5-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d6e5-123">name</span><span class="sxs-lookup"><span data-stu-id="9d6e5-123">Name</span></span>|`xs:string`|<span data-ttu-id="9d6e5-124">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="9d6e5-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="9d6e5-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="9d6e5-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9d6e5-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9d6e5-128">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9d6e5-129">Payload</span><span class="sxs-lookup"><span data-stu-id="9d6e5-129">Payload</span></span>|`xs:string`|<span data-ttu-id="9d6e5-130">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="9d6e5-130">The user-defined payload of the event.</span></span>|
