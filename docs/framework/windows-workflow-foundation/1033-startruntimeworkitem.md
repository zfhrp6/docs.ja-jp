---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510067"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="6edcb-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="6edcb-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6edcb-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6edcb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6edcb-104">ID</span><span class="sxs-lookup"><span data-stu-id="6edcb-104">ID</span></span>|<span data-ttu-id="6edcb-105">1033</span><span class="sxs-lookup"><span data-stu-id="6edcb-105">1033</span></span>|  
|<span data-ttu-id="6edcb-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6edcb-106">Keywords</span></span>|<span data-ttu-id="6edcb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6edcb-107">WFRuntime</span></span>|  
|<span data-ttu-id="6edcb-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6edcb-108">Level</span></span>|<span data-ttu-id="6edcb-109">詳細</span><span class="sxs-lookup"><span data-stu-id="6edcb-109">Verbose</span></span>|  
|<span data-ttu-id="6edcb-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6edcb-110">Channel</span></span>|<span data-ttu-id="6edcb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6edcb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6edcb-112">説明</span><span class="sxs-lookup"><span data-stu-id="6edcb-112">Description</span></span>  
 <span data-ttu-id="6edcb-113">RuntimeWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="6edcb-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6edcb-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6edcb-114">Message</span></span>  
 <span data-ttu-id="6edcb-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="6edcb-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6edcb-116">詳細</span><span class="sxs-lookup"><span data-stu-id="6edcb-116">Details</span></span>  
  
|<span data-ttu-id="6edcb-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6edcb-117">Data Item Name</span></span>|<span data-ttu-id="6edcb-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6edcb-118">Data Item Type</span></span>|<span data-ttu-id="6edcb-119">説明</span><span class="sxs-lookup"><span data-stu-id="6edcb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6edcb-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="6edcb-120">Activity</span></span>|<span data-ttu-id="6edcb-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6edcb-121">xs:string</span></span>|<span data-ttu-id="6edcb-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="6edcb-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="6edcb-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6edcb-123">DisplayName</span></span>|<span data-ttu-id="6edcb-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6edcb-124">xs:string</span></span>|<span data-ttu-id="6edcb-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="6edcb-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="6edcb-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6edcb-126">InstanceId</span></span>|<span data-ttu-id="6edcb-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6edcb-127">xs:string</span></span>|<span data-ttu-id="6edcb-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="6edcb-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6edcb-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6edcb-129">AppDomain</span></span>|<span data-ttu-id="6edcb-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6edcb-130">xs:string</span></span>|<span data-ttu-id="6edcb-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6edcb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
