---
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459141"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="eff62-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="eff62-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="eff62-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="eff62-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eff62-104">ID</span><span class="sxs-lookup"><span data-stu-id="eff62-104">ID</span></span>|<span data-ttu-id="eff62-105">303</span><span class="sxs-lookup"><span data-stu-id="eff62-105">303</span></span>|  
|<span data-ttu-id="eff62-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="eff62-106">Keywords</span></span>|<span data-ttu-id="eff62-107">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="eff62-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="eff62-108">レベル</span><span class="sxs-lookup"><span data-stu-id="eff62-108">Level</span></span>|<span data-ttu-id="eff62-109">情報</span><span class="sxs-lookup"><span data-stu-id="eff62-109">Information</span></span>|  
|<span data-ttu-id="eff62-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="eff62-110">Channel</span></span>|<span data-ttu-id="eff62-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="eff62-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eff62-112">説明</span><span class="sxs-lookup"><span data-stu-id="eff62-112">Description</span></span>  
 <span data-ttu-id="eff62-113">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="eff62-113">This event is emitted from user code.</span></span> <span data-ttu-id="eff62-114">開発者は、カスタム定義の情報イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="eff62-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="eff62-115">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="eff62-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="eff62-116">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="eff62-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eff62-117">メッセージ</span><span class="sxs-lookup"><span data-stu-id="eff62-117">Message</span></span>  
 <span data-ttu-id="eff62-118">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="eff62-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="eff62-119">説明</span><span class="sxs-lookup"><span data-stu-id="eff62-119">Details</span></span>  
  
|<span data-ttu-id="eff62-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="eff62-120">Data Item Name</span></span>|<span data-ttu-id="eff62-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="eff62-121">Data Item Type</span></span>|<span data-ttu-id="eff62-122">説明</span><span class="sxs-lookup"><span data-stu-id="eff62-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eff62-123">名前</span><span class="sxs-lookup"><span data-stu-id="eff62-123">Name</span></span>|`xs:string`|<span data-ttu-id="eff62-124">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="eff62-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="eff62-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="eff62-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="eff62-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="eff62-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="eff62-127">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="eff62-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="eff62-128">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="eff62-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="eff62-129">Payload</span><span class="sxs-lookup"><span data-stu-id="eff62-129">Payload</span></span>|`xs:string`|<span data-ttu-id="eff62-130">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="eff62-130">The user-defined payload of the event.</span></span>|
