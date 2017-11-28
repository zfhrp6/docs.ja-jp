---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="6be5d-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="6be5d-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="6be5d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6be5d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6be5d-104">ID</span><span class="sxs-lookup"><span data-stu-id="6be5d-104">ID</span></span>|<span data-ttu-id="6be5d-105">4203</span><span class="sxs-lookup"><span data-stu-id="6be5d-105">4203</span></span>|  
|<span data-ttu-id="6be5d-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6be5d-106">Keywords</span></span>|<span data-ttu-id="6be5d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="6be5d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="6be5d-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6be5d-108">Level</span></span>|<span data-ttu-id="6be5d-109">Error</span><span class="sxs-lookup"><span data-stu-id="6be5d-109">Error</span></span>|  
|<span data-ttu-id="6be5d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6be5d-110">Channel</span></span>|<span data-ttu-id="6be5d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6be5d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6be5d-112">説明</span><span class="sxs-lookup"><span data-stu-id="6be5d-112">Description</span></span>  
 <span data-ttu-id="6be5d-113">ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="6be5d-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="6be5d-114">SqlWorkflowInstanceStore は中止されます。</span><span class="sxs-lookup"><span data-stu-id="6be5d-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6be5d-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6be5d-115">Message</span></span>  
 <span data-ttu-id="6be5d-116">ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。</span><span class="sxs-lookup"><span data-stu-id="6be5d-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="6be5d-117">SqlWorkflowInstanceStore を中止します。</span><span class="sxs-lookup"><span data-stu-id="6be5d-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6be5d-118">詳細</span><span class="sxs-lookup"><span data-stu-id="6be5d-118">Details</span></span>  
  
|<span data-ttu-id="6be5d-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6be5d-119">Data Item Name</span></span>|<span data-ttu-id="6be5d-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6be5d-120">Data Item Type</span></span>|<span data-ttu-id="6be5d-121">説明</span><span class="sxs-lookup"><span data-stu-id="6be5d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6be5d-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6be5d-122">AppDomain</span></span>|<span data-ttu-id="6be5d-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="6be5d-123">xs:string</span></span>|<span data-ttu-id="6be5d-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6be5d-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
