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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c2214ec48f0c1cba1e3aacad0eaa5a29625f9c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="77dc3-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="77dc3-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="77dc3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="77dc3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77dc3-104">ID</span><span class="sxs-lookup"><span data-stu-id="77dc3-104">ID</span></span>|<span data-ttu-id="77dc3-105">4203</span><span class="sxs-lookup"><span data-stu-id="77dc3-105">4203</span></span>|  
|<span data-ttu-id="77dc3-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="77dc3-106">Keywords</span></span>|<span data-ttu-id="77dc3-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="77dc3-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="77dc3-108">レベル</span><span class="sxs-lookup"><span data-stu-id="77dc3-108">Level</span></span>|<span data-ttu-id="77dc3-109">Error</span><span class="sxs-lookup"><span data-stu-id="77dc3-109">Error</span></span>|  
|<span data-ttu-id="77dc3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="77dc3-110">Channel</span></span>|<span data-ttu-id="77dc3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="77dc3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77dc3-112">説明</span><span class="sxs-lookup"><span data-stu-id="77dc3-112">Description</span></span>  
 <span data-ttu-id="77dc3-113">ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="77dc3-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="77dc3-114">SqlWorkflowInstanceStore は中止されます。</span><span class="sxs-lookup"><span data-stu-id="77dc3-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77dc3-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="77dc3-115">Message</span></span>  
 <span data-ttu-id="77dc3-116">ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。</span><span class="sxs-lookup"><span data-stu-id="77dc3-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="77dc3-117">SqlWorkflowInstanceStore を中止します。</span><span class="sxs-lookup"><span data-stu-id="77dc3-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77dc3-118">詳細</span><span class="sxs-lookup"><span data-stu-id="77dc3-118">Details</span></span>  
  
|<span data-ttu-id="77dc3-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="77dc3-119">Data Item Name</span></span>|<span data-ttu-id="77dc3-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="77dc3-120">Data Item Type</span></span>|<span data-ttu-id="77dc3-121">説明</span><span class="sxs-lookup"><span data-stu-id="77dc3-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77dc3-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="77dc3-122">AppDomain</span></span>|<span data-ttu-id="77dc3-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="77dc3-123">xs:string</span></span>|<span data-ttu-id="77dc3-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="77dc3-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
