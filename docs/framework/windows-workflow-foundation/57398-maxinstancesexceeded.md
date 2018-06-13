---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512552"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="a70b0-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="a70b0-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="a70b0-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a70b0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a70b0-104">ID</span><span class="sxs-lookup"><span data-stu-id="a70b0-104">ID</span></span>|<span data-ttu-id="a70b0-105">57398</span><span class="sxs-lookup"><span data-stu-id="a70b0-105">57398</span></span>|  
|<span data-ttu-id="a70b0-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a70b0-106">Keywords</span></span>|<span data-ttu-id="a70b0-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a70b0-107">WFServices</span></span>|  
|<span data-ttu-id="a70b0-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a70b0-108">Level</span></span>|<span data-ttu-id="a70b0-109">警告</span><span class="sxs-lookup"><span data-stu-id="a70b0-109">Warning</span></span>|  
|<span data-ttu-id="a70b0-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a70b0-110">Channel</span></span>|<span data-ttu-id="a70b0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a70b0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a70b0-112">説明</span><span class="sxs-lookup"><span data-stu-id="a70b0-112">Description</span></span>  
 <span data-ttu-id="a70b0-113">システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="a70b0-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a70b0-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a70b0-114">Message</span></span>  
 <span data-ttu-id="a70b0-115">システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="a70b0-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="a70b0-116">このスロットルの制限は %1 に設定されました。</span><span class="sxs-lookup"><span data-stu-id="a70b0-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="a70b0-117">スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a70b0-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a70b0-118">詳細</span><span class="sxs-lookup"><span data-stu-id="a70b0-118">Details</span></span>  
  
|<span data-ttu-id="a70b0-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a70b0-119">Data Item Name</span></span>|<span data-ttu-id="a70b0-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a70b0-120">Data Item Type</span></span>|<span data-ttu-id="a70b0-121">説明</span><span class="sxs-lookup"><span data-stu-id="a70b0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a70b0-122">名前</span><span class="sxs-lookup"><span data-stu-id="a70b0-122">Name</span></span>|<span data-ttu-id="a70b0-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a70b0-123">xs:string</span></span>|<span data-ttu-id="a70b0-124">項目の名前。</span><span class="sxs-lookup"><span data-stu-id="a70b0-124">The name of the item.</span></span>|  
|<span data-ttu-id="a70b0-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a70b0-125">AppDomain</span></span>|<span data-ttu-id="a70b0-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a70b0-126">xs:string</span></span>|<span data-ttu-id="a70b0-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a70b0-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
