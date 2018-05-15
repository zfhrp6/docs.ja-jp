---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="c9145-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="c9145-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="c9145-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c9145-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9145-104">ID</span><span class="sxs-lookup"><span data-stu-id="c9145-104">ID</span></span>|<span data-ttu-id="c9145-105">1036</span><span class="sxs-lookup"><span data-stu-id="c9145-105">1036</span></span>|  
|<span data-ttu-id="c9145-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c9145-106">Keywords</span></span>|<span data-ttu-id="c9145-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9145-107">WFRuntime</span></span>|  
|<span data-ttu-id="c9145-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c9145-108">Level</span></span>|<span data-ttu-id="c9145-109">詳細</span><span class="sxs-lookup"><span data-stu-id="c9145-109">Verbose</span></span>|  
|<span data-ttu-id="c9145-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c9145-110">Channel</span></span>|<span data-ttu-id="c9145-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c9145-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9145-112">説明</span><span class="sxs-lookup"><span data-stu-id="c9145-112">Description</span></span>  
 <span data-ttu-id="c9145-113">アクティビティがランタイムのトランザクションの完了をスケジュールしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c9145-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9145-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c9145-114">Message</span></span>  
 <span data-ttu-id="c9145-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' はランタイム トランザクションの完了をスケジュールしました。</span><span class="sxs-lookup"><span data-stu-id="c9145-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9145-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c9145-116">Details</span></span>  
  
|<span data-ttu-id="c9145-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c9145-117">Data Item Name</span></span>|<span data-ttu-id="c9145-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c9145-118">Data Item Type</span></span>|<span data-ttu-id="c9145-119">説明</span><span class="sxs-lookup"><span data-stu-id="c9145-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9145-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="c9145-120">Activity</span></span>|<span data-ttu-id="c9145-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9145-121">xs:string</span></span>|<span data-ttu-id="c9145-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c9145-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c9145-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c9145-123">DisplayName</span></span>|<span data-ttu-id="c9145-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9145-124">xs:string</span></span>|<span data-ttu-id="c9145-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c9145-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c9145-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c9145-126">InstanceId</span></span>|<span data-ttu-id="c9145-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9145-127">xs:string</span></span>|<span data-ttu-id="c9145-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c9145-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c9145-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9145-129">AppDomain</span></span>|<span data-ttu-id="c9145-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9145-130">xs:string</span></span>|<span data-ttu-id="c9145-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c9145-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
