---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="7493c-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="7493c-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="7493c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7493c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7493c-104">ID</span><span class="sxs-lookup"><span data-stu-id="7493c-104">ID</span></span>|<span data-ttu-id="7493c-105">4209</span><span class="sxs-lookup"><span data-stu-id="7493c-105">4209</span></span>|  
|<span data-ttu-id="7493c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7493c-106">Keywords</span></span>|<span data-ttu-id="7493c-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="7493c-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="7493c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7493c-108">Level</span></span>|<span data-ttu-id="7493c-109">Error</span><span class="sxs-lookup"><span data-stu-id="7493c-109">Error</span></span>|  
|<span data-ttu-id="7493c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7493c-110">Channel</span></span>|<span data-ttu-id="7493c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7493c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7493c-112">説明</span><span class="sxs-lookup"><span data-stu-id="7493c-112">Description</span></span>  
 <span data-ttu-id="7493c-113">SQL 接続を開こうとしてタイムアウトが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7493c-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7493c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7493c-114">Message</span></span>  
 <span data-ttu-id="7493c-115">SQL 接続を開こうとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7493c-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="7493c-116">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="7493c-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="7493c-117">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7493c-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7493c-118">詳細</span><span class="sxs-lookup"><span data-stu-id="7493c-118">Details</span></span>  
  
|<span data-ttu-id="7493c-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7493c-119">Data Item Name</span></span>|<span data-ttu-id="7493c-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7493c-120">Data Item Type</span></span>|<span data-ttu-id="7493c-121">説明</span><span class="sxs-lookup"><span data-stu-id="7493c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7493c-122">Timeout</span><span class="sxs-lookup"><span data-stu-id="7493c-122">Timeout</span></span>|<span data-ttu-id="7493c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7493c-123">xs:string</span></span>|<span data-ttu-id="7493c-124">SQL 接続を開く場合のタイムアウト値。</span><span class="sxs-lookup"><span data-stu-id="7493c-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="7493c-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7493c-125">AppDomain</span></span>|<span data-ttu-id="7493c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7493c-126">xs:string</span></span>|<span data-ttu-id="7493c-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7493c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
