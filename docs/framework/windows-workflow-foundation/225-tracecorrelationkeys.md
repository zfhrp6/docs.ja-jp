---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512139"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="5a7fd-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="5a7fd-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="5a7fd-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5a7fd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a7fd-104">ID</span><span class="sxs-lookup"><span data-stu-id="5a7fd-104">ID</span></span>|<span data-ttu-id="5a7fd-105">225</span><span class="sxs-lookup"><span data-stu-id="5a7fd-105">225</span></span>|  
|<span data-ttu-id="5a7fd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="5a7fd-106">Keywords</span></span>|<span data-ttu-id="5a7fd-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5a7fd-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5a7fd-108">レベル</span><span class="sxs-lookup"><span data-stu-id="5a7fd-108">Level</span></span>|<span data-ttu-id="5a7fd-109">情報</span><span class="sxs-lookup"><span data-stu-id="5a7fd-109">Information</span></span>|  
|<span data-ttu-id="5a7fd-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5a7fd-110">Channel</span></span>|<span data-ttu-id="5a7fd-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5a7fd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5a7fd-112">説明</span><span class="sxs-lookup"><span data-stu-id="5a7fd-112">Description</span></span>  
 <span data-ttu-id="5a7fd-113">このイベントは、ワークフロー サービスでコンテンツ ベースの相関関係が使用されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="5a7fd-114">これには、メッセージとインスタンスの相関関係を定義するために適用されている相関関係キーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5a7fd-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="5a7fd-115">Message</span></span>  
 <span data-ttu-id="5a7fd-116">親スコープ '%3' の値 '%2' を使用して相関関係キー '%1' が計算されました。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5a7fd-117">詳細</span><span class="sxs-lookup"><span data-stu-id="5a7fd-117">Details</span></span>  
  
|<span data-ttu-id="5a7fd-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5a7fd-118">Data Item Name</span></span>|<span data-ttu-id="5a7fd-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5a7fd-119">Data Item Type</span></span>|<span data-ttu-id="5a7fd-120">説明</span><span class="sxs-lookup"><span data-stu-id="5a7fd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5a7fd-121">Instance Key</span><span class="sxs-lookup"><span data-stu-id="5a7fd-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="5a7fd-122">相関関係値から生成されたキー。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="5a7fd-123">値</span><span class="sxs-lookup"><span data-stu-id="5a7fd-123">Values</span></span>|`xs:string`|<span data-ttu-id="5a7fd-124">相関関係インスタンス キーの計算に使用された値。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="5a7fd-125">Parent Scope</span><span class="sxs-lookup"><span data-stu-id="5a7fd-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="5a7fd-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="5a7fd-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="5a7fd-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5a7fd-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5a7fd-129">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5a7fd-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5a7fd-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5a7fd-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5a7fd-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
