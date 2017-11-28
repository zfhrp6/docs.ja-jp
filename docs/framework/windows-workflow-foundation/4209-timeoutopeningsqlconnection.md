---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f87e99585ccbdf3b89653f026860e7b66dc6c9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="17053-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="17053-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="17053-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="17053-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17053-104">ID</span><span class="sxs-lookup"><span data-stu-id="17053-104">ID</span></span>|<span data-ttu-id="17053-105">4209</span><span class="sxs-lookup"><span data-stu-id="17053-105">4209</span></span>|  
|<span data-ttu-id="17053-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="17053-106">Keywords</span></span>|<span data-ttu-id="17053-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="17053-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="17053-108">レベル</span><span class="sxs-lookup"><span data-stu-id="17053-108">Level</span></span>|<span data-ttu-id="17053-109">Error</span><span class="sxs-lookup"><span data-stu-id="17053-109">Error</span></span>|  
|<span data-ttu-id="17053-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="17053-110">Channel</span></span>|<span data-ttu-id="17053-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="17053-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17053-112">説明</span><span class="sxs-lookup"><span data-stu-id="17053-112">Description</span></span>  
 <span data-ttu-id="17053-113">SQL 接続を開こうとしてタイムアウトが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="17053-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17053-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="17053-114">Message</span></span>  
 <span data-ttu-id="17053-115">SQL 接続を開こうとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="17053-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="17053-116">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="17053-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="17053-117">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17053-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17053-118">詳細</span><span class="sxs-lookup"><span data-stu-id="17053-118">Details</span></span>  
  
|<span data-ttu-id="17053-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="17053-119">Data Item Name</span></span>|<span data-ttu-id="17053-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="17053-120">Data Item Type</span></span>|<span data-ttu-id="17053-121">説明</span><span class="sxs-lookup"><span data-stu-id="17053-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17053-122">Timeout</span><span class="sxs-lookup"><span data-stu-id="17053-122">Timeout</span></span>|<span data-ttu-id="17053-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="17053-123">xs:string</span></span>|<span data-ttu-id="17053-124">SQL 接続を開く場合のタイムアウト値。</span><span class="sxs-lookup"><span data-stu-id="17053-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="17053-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="17053-125">AppDomain</span></span>|<span data-ttu-id="17053-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="17053-126">xs:string</span></span>|<span data-ttu-id="17053-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="17053-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
