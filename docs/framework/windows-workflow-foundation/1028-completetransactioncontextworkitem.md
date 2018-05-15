---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="58d80-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="58d80-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="58d80-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="58d80-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58d80-104">ID</span><span class="sxs-lookup"><span data-stu-id="58d80-104">ID</span></span>|<span data-ttu-id="58d80-105">1028</span><span class="sxs-lookup"><span data-stu-id="58d80-105">1028</span></span>|  
|<span data-ttu-id="58d80-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="58d80-106">Keywords</span></span>|<span data-ttu-id="58d80-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="58d80-107">WFRuntime</span></span>|  
|<span data-ttu-id="58d80-108">レベル</span><span class="sxs-lookup"><span data-stu-id="58d80-108">Level</span></span>|<span data-ttu-id="58d80-109">詳細</span><span class="sxs-lookup"><span data-stu-id="58d80-109">Verbose</span></span>|  
|<span data-ttu-id="58d80-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="58d80-110">Channel</span></span>|<span data-ttu-id="58d80-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="58d80-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58d80-112">説明</span><span class="sxs-lookup"><span data-stu-id="58d80-112">Description</span></span>  
 <span data-ttu-id="58d80-113">TransactionContextWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="58d80-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58d80-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="58d80-114">Message</span></span>  
 <span data-ttu-id="58d80-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="58d80-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58d80-116">詳細</span><span class="sxs-lookup"><span data-stu-id="58d80-116">Details</span></span>  
  
|<span data-ttu-id="58d80-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="58d80-117">Data Item Name</span></span>|<span data-ttu-id="58d80-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="58d80-118">Data Item Type</span></span>|<span data-ttu-id="58d80-119">説明</span><span class="sxs-lookup"><span data-stu-id="58d80-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58d80-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="58d80-120">Activity</span></span>|<span data-ttu-id="58d80-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="58d80-121">xs:string</span></span>|<span data-ttu-id="58d80-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="58d80-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="58d80-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="58d80-123">DisplayName</span></span>|<span data-ttu-id="58d80-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="58d80-124">xs:string</span></span>|<span data-ttu-id="58d80-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="58d80-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="58d80-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="58d80-126">InstanceId</span></span>|<span data-ttu-id="58d80-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="58d80-127">xs:string</span></span>|<span data-ttu-id="58d80-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="58d80-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="58d80-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="58d80-129">AppDomain</span></span>|<span data-ttu-id="58d80-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="58d80-130">xs:string</span></span>|<span data-ttu-id="58d80-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="58d80-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
