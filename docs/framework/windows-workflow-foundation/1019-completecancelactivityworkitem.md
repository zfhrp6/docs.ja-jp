---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 28d19742055c51ca94c36ffddf15dced7dfc14cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510209"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="2ebc1-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="2ebc1-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2ebc1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2ebc1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ebc1-104">ID</span><span class="sxs-lookup"><span data-stu-id="2ebc1-104">ID</span></span>|<span data-ttu-id="2ebc1-105">1019</span><span class="sxs-lookup"><span data-stu-id="2ebc1-105">1019</span></span>|  
|<span data-ttu-id="2ebc1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2ebc1-106">Keywords</span></span>|<span data-ttu-id="2ebc1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2ebc1-107">WFRuntime</span></span>|  
|<span data-ttu-id="2ebc1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2ebc1-108">Level</span></span>|<span data-ttu-id="2ebc1-109">詳細</span><span class="sxs-lookup"><span data-stu-id="2ebc1-109">Verbose</span></span>|  
|<span data-ttu-id="2ebc1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2ebc1-110">Channel</span></span>|<span data-ttu-id="2ebc1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2ebc1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2ebc1-112">説明</span><span class="sxs-lookup"><span data-stu-id="2ebc1-112">Description</span></span>  
 <span data-ttu-id="2ebc1-113">CancelActivityWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="2ebc1-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2ebc1-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2ebc1-114">Message</span></span>  
 <span data-ttu-id="2ebc1-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="2ebc1-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2ebc1-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2ebc1-116">Details</span></span>  
  
|<span data-ttu-id="2ebc1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2ebc1-117">Data Item Name</span></span>|<span data-ttu-id="2ebc1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2ebc1-118">Data Item Type</span></span>|<span data-ttu-id="2ebc1-119">説明</span><span class="sxs-lookup"><span data-stu-id="2ebc1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2ebc1-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2ebc1-120">Activity</span></span>|<span data-ttu-id="2ebc1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ebc1-121">xs:string</span></span>|<span data-ttu-id="2ebc1-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="2ebc1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2ebc1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2ebc1-123">DisplayName</span></span>|<span data-ttu-id="2ebc1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ebc1-124">xs:string</span></span>|<span data-ttu-id="2ebc1-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2ebc1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2ebc1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2ebc1-126">InstanceId</span></span>|<span data-ttu-id="2ebc1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ebc1-127">xs:string</span></span>|<span data-ttu-id="2ebc1-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="2ebc1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2ebc1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2ebc1-129">AppDomain</span></span>|<span data-ttu-id="2ebc1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ebc1-130">xs:string</span></span>|<span data-ttu-id="2ebc1-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2ebc1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
