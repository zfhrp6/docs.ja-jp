---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458475"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="7ab93-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="7ab93-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="7ab93-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7ab93-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ab93-104">ID</span><span class="sxs-lookup"><span data-stu-id="7ab93-104">ID</span></span>|<span data-ttu-id="7ab93-105">213</span><span class="sxs-lookup"><span data-stu-id="7ab93-105">213</span></span>|  
|<span data-ttu-id="7ab93-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7ab93-106">Keywords</span></span>|<span data-ttu-id="7ab93-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceHost</span><span class="sxs-lookup"><span data-stu-id="7ab93-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="7ab93-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7ab93-108">Level</span></span>|<span data-ttu-id="7ab93-109">LogAlways (常にログ)</span><span class="sxs-lookup"><span data-stu-id="7ab93-109">LogAlways</span></span>|  
|<span data-ttu-id="7ab93-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7ab93-110">Channel</span></span>|<span data-ttu-id="7ab93-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7ab93-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7ab93-112">説明</span><span class="sxs-lookup"><span data-stu-id="7ab93-112">Description</span></span>  
 <span data-ttu-id="7ab93-113">このイベントは、Web でホストされているサービス ホストが起動されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="7ab93-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="7ab93-114">通常、サービスがメッセージによってアクティブにされた時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="7ab93-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="7ab93-115">また、サービスが自動的に開始するように構成されている場合も発生します。</span><span class="sxs-lookup"><span data-stu-id="7ab93-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7ab93-116">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7ab93-116">Message</span></span>  
 <span data-ttu-id="7ab93-117">ServiceHost は '%1' で開始されています。</span><span class="sxs-lookup"><span data-stu-id="7ab93-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7ab93-118">説明</span><span class="sxs-lookup"><span data-stu-id="7ab93-118">Details</span></span>  
  
|<span data-ttu-id="7ab93-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7ab93-119">Data Item Name</span></span>|<span data-ttu-id="7ab93-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7ab93-120">Data Item Type</span></span>|<span data-ttu-id="7ab93-121">説明</span><span class="sxs-lookup"><span data-stu-id="7ab93-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7ab93-122">Service Type Name</span><span class="sxs-lookup"><span data-stu-id="7ab93-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="7ab93-123">サービス実装の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="7ab93-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="7ab93-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="7ab93-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="7ab93-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="7ab93-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7ab93-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="7ab93-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7ab93-127">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="7ab93-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7ab93-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7ab93-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7ab93-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7ab93-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
