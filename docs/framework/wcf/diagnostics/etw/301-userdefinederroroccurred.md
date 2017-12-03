---
title: 301 - UserDefinedErrorOccurred
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56cfe60c221062e3ad7ae1b8cbdc9b135e6fa2e8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="d7efa-102">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="d7efa-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="d7efa-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d7efa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7efa-104">ID</span><span class="sxs-lookup"><span data-stu-id="d7efa-104">ID</span></span>|<span data-ttu-id="d7efa-105">301</span><span class="sxs-lookup"><span data-stu-id="d7efa-105">301</span></span>|  
|<span data-ttu-id="d7efa-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d7efa-106">Keywords</span></span>|<span data-ttu-id="d7efa-107">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="d7efa-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="d7efa-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d7efa-108">Level</span></span>|<span data-ttu-id="d7efa-109">Error</span><span class="sxs-lookup"><span data-stu-id="d7efa-109">Error</span></span>|  
|<span data-ttu-id="d7efa-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d7efa-110">Channel</span></span>|<span data-ttu-id="d7efa-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d7efa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d7efa-112">説明</span><span class="sxs-lookup"><span data-stu-id="d7efa-112">Description</span></span>  
 <span data-ttu-id="d7efa-113">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="d7efa-113">This event is emitted from user code.</span></span> <span data-ttu-id="d7efa-114">開発者は、カスタム定義のエラー イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d7efa-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="d7efa-115">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="d7efa-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="d7efa-116">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="d7efa-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d7efa-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d7efa-117">Message</span></span>  
 <span data-ttu-id="d7efa-118">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="d7efa-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="d7efa-119">詳細</span><span class="sxs-lookup"><span data-stu-id="d7efa-119">Details</span></span>  
  
|<span data-ttu-id="d7efa-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d7efa-120">Data Item Name</span></span>|<span data-ttu-id="d7efa-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d7efa-121">Data Item Type</span></span>|<span data-ttu-id="d7efa-122">説明</span><span class="sxs-lookup"><span data-stu-id="d7efa-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d7efa-123">名前</span><span class="sxs-lookup"><span data-stu-id="d7efa-123">Name</span></span>|`xs:string`|<span data-ttu-id="d7efa-124">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="d7efa-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="d7efa-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="d7efa-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="d7efa-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="d7efa-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d7efa-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="d7efa-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d7efa-128">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="d7efa-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d7efa-129">Payload</span><span class="sxs-lookup"><span data-stu-id="d7efa-129">Payload</span></span>|`xs:string`|<span data-ttu-id="d7efa-130">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="d7efa-130">The user-defined payload of the event.</span></span>|
