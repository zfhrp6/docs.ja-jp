---
title: 1037 - RuntimeTransactionComplete
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31333ddeca7a6ef555413d09864e55834ff4a2b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1037---runtimetransactioncomplete"></a><span data-ttu-id="8c3f7-102">1037 - RuntimeTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="8c3f7-102">1037 - RuntimeTransactionComplete</span></span>
## <a name="properties"></a><span data-ttu-id="8c3f7-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c3f7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c3f7-104">ID</span><span class="sxs-lookup"><span data-stu-id="8c3f7-104">ID</span></span>|<span data-ttu-id="8c3f7-105">1037</span><span class="sxs-lookup"><span data-stu-id="8c3f7-105">1037</span></span>|  
|<span data-ttu-id="8c3f7-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="8c3f7-106">Keywords</span></span>|<span data-ttu-id="8c3f7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8c3f7-107">WFRuntime</span></span>|  
|<span data-ttu-id="8c3f7-108">レベル</span><span class="sxs-lookup"><span data-stu-id="8c3f7-108">Level</span></span>|<span data-ttu-id="8c3f7-109">詳細</span><span class="sxs-lookup"><span data-stu-id="8c3f7-109">Verbose</span></span>|  
|<span data-ttu-id="8c3f7-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8c3f7-110">Channel</span></span>|<span data-ttu-id="8c3f7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8c3f7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c3f7-112">説明</span><span class="sxs-lookup"><span data-stu-id="8c3f7-112">Description</span></span>  
 <span data-ttu-id="8c3f7-113">ランタイム トランザクションが完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8c3f7-113">Indicates the runtime transaction has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c3f7-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="8c3f7-114">Message</span></span>  
 <span data-ttu-id="8c3f7-115">ランタイム トランザクションは '%1' の状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="8c3f7-115">The runtime transaction has completed with the state '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c3f7-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8c3f7-116">Details</span></span>  
  
|<span data-ttu-id="8c3f7-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8c3f7-117">Data Item Name</span></span>|<span data-ttu-id="8c3f7-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8c3f7-118">Data Item Type</span></span>|<span data-ttu-id="8c3f7-119">説明</span><span class="sxs-lookup"><span data-stu-id="8c3f7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c3f7-120">状態</span><span class="sxs-lookup"><span data-stu-id="8c3f7-120">State</span></span>|<span data-ttu-id="8c3f7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c3f7-121">xs:string</span></span>|<span data-ttu-id="8c3f7-122">トランザクションの状態。</span><span class="sxs-lookup"><span data-stu-id="8c3f7-122">The state of the transaction.</span></span>|  
|<span data-ttu-id="8c3f7-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c3f7-123">AppDomain</span></span>|<span data-ttu-id="8c3f7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c3f7-124">xs:string</span></span>|<span data-ttu-id="8c3f7-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8c3f7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
