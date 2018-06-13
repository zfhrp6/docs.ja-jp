---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510173"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="8ed0c-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="8ed0c-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8ed0c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ed0c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ed0c-104">ID</span><span class="sxs-lookup"><span data-stu-id="8ed0c-104">ID</span></span>|<span data-ttu-id="8ed0c-105">1017</span><span class="sxs-lookup"><span data-stu-id="8ed0c-105">1017</span></span>|  
|<span data-ttu-id="8ed0c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="8ed0c-106">Keywords</span></span>|<span data-ttu-id="8ed0c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8ed0c-107">WFRuntime</span></span>|  
|<span data-ttu-id="8ed0c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="8ed0c-108">Level</span></span>|<span data-ttu-id="8ed0c-109">詳細</span><span class="sxs-lookup"><span data-stu-id="8ed0c-109">Verbose</span></span>|  
|<span data-ttu-id="8ed0c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8ed0c-110">Channel</span></span>|<span data-ttu-id="8ed0c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8ed0c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8ed0c-112">説明</span><span class="sxs-lookup"><span data-stu-id="8ed0c-112">Description</span></span>  
 <span data-ttu-id="8ed0c-113">CancelActivityWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="8ed0c-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8ed0c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="8ed0c-114">Message</span></span>  
 <span data-ttu-id="8ed0c-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="8ed0c-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8ed0c-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8ed0c-116">Details</span></span>  
  
|<span data-ttu-id="8ed0c-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8ed0c-117">Data Item Name</span></span>|<span data-ttu-id="8ed0c-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8ed0c-118">Data Item Type</span></span>|<span data-ttu-id="8ed0c-119">説明</span><span class="sxs-lookup"><span data-stu-id="8ed0c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8ed0c-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="8ed0c-120">Activity</span></span>|<span data-ttu-id="8ed0c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ed0c-121">xs:string</span></span>|<span data-ttu-id="8ed0c-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="8ed0c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8ed0c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8ed0c-123">DisplayName</span></span>|<span data-ttu-id="8ed0c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ed0c-124">xs:string</span></span>|<span data-ttu-id="8ed0c-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="8ed0c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8ed0c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8ed0c-126">InstanceId</span></span>|<span data-ttu-id="8ed0c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ed0c-127">xs:string</span></span>|<span data-ttu-id="8ed0c-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="8ed0c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8ed0c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8ed0c-129">AppDomain</span></span>|<span data-ttu-id="8ed0c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ed0c-130">xs:string</span></span>|<span data-ttu-id="8ed0c-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8ed0c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
