---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="7f857-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="7f857-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="7f857-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7f857-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f857-104">ID</span><span class="sxs-lookup"><span data-stu-id="7f857-104">ID</span></span>|<span data-ttu-id="7f857-105">4203</span><span class="sxs-lookup"><span data-stu-id="7f857-105">4203</span></span>|  
|<span data-ttu-id="7f857-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7f857-106">Keywords</span></span>|<span data-ttu-id="7f857-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="7f857-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="7f857-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7f857-108">Level</span></span>|<span data-ttu-id="7f857-109">Error</span><span class="sxs-lookup"><span data-stu-id="7f857-109">Error</span></span>|  
|<span data-ttu-id="7f857-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7f857-110">Channel</span></span>|<span data-ttu-id="7f857-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7f857-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f857-112">説明</span><span class="sxs-lookup"><span data-stu-id="7f857-112">Description</span></span>  
 <span data-ttu-id="7f857-113">ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="7f857-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="7f857-114">SqlWorkflowInstanceStore は中止されます。</span><span class="sxs-lookup"><span data-stu-id="7f857-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f857-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7f857-115">Message</span></span>  
 <span data-ttu-id="7f857-116">ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。</span><span class="sxs-lookup"><span data-stu-id="7f857-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="7f857-117">SqlWorkflowInstanceStore を中止します。</span><span class="sxs-lookup"><span data-stu-id="7f857-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f857-118">詳細</span><span class="sxs-lookup"><span data-stu-id="7f857-118">Details</span></span>  
  
|<span data-ttu-id="7f857-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7f857-119">Data Item Name</span></span>|<span data-ttu-id="7f857-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7f857-120">Data Item Type</span></span>|<span data-ttu-id="7f857-121">説明</span><span class="sxs-lookup"><span data-stu-id="7f857-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f857-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7f857-122">AppDomain</span></span>|<span data-ttu-id="7f857-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f857-123">xs:string</span></span>|<span data-ttu-id="7f857-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7f857-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
