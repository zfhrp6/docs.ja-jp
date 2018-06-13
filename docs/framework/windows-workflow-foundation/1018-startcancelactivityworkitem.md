---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510654"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="e7ebe-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="e7ebe-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e7ebe-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e7ebe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7ebe-104">ID</span><span class="sxs-lookup"><span data-stu-id="e7ebe-104">ID</span></span>|<span data-ttu-id="e7ebe-105">1018</span><span class="sxs-lookup"><span data-stu-id="e7ebe-105">1018</span></span>|  
|<span data-ttu-id="e7ebe-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e7ebe-106">Keywords</span></span>|<span data-ttu-id="e7ebe-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e7ebe-107">WFRuntime</span></span>|  
|<span data-ttu-id="e7ebe-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e7ebe-108">Level</span></span>|<span data-ttu-id="e7ebe-109">詳細</span><span class="sxs-lookup"><span data-stu-id="e7ebe-109">Verbose</span></span>|  
|<span data-ttu-id="e7ebe-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e7ebe-110">Channel</span></span>|<span data-ttu-id="e7ebe-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e7ebe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e7ebe-112">説明</span><span class="sxs-lookup"><span data-stu-id="e7ebe-112">Description</span></span>  
 <span data-ttu-id="e7ebe-113">CancelActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="e7ebe-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e7ebe-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e7ebe-114">Message</span></span>  
 <span data-ttu-id="e7ebe-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="e7ebe-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e7ebe-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e7ebe-116">Details</span></span>  
  
|<span data-ttu-id="e7ebe-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e7ebe-117">Data Item Name</span></span>|<span data-ttu-id="e7ebe-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e7ebe-118">Data Item Type</span></span>|<span data-ttu-id="e7ebe-119">説明</span><span class="sxs-lookup"><span data-stu-id="e7ebe-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e7ebe-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e7ebe-120">Activity</span></span>|<span data-ttu-id="e7ebe-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e7ebe-121">xs:string</span></span>|<span data-ttu-id="e7ebe-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="e7ebe-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e7ebe-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e7ebe-123">DisplayName</span></span>|<span data-ttu-id="e7ebe-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e7ebe-124">xs:string</span></span>|<span data-ttu-id="e7ebe-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="e7ebe-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e7ebe-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e7ebe-126">InstanceId</span></span>|<span data-ttu-id="e7ebe-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e7ebe-127">xs:string</span></span>|<span data-ttu-id="e7ebe-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="e7ebe-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e7ebe-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e7ebe-129">AppDomain</span></span>|<span data-ttu-id="e7ebe-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e7ebe-130">xs:string</span></span>|<span data-ttu-id="e7ebe-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e7ebe-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
