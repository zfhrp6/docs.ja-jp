---
title: 4202 - StartSqlCommandExecute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 79cffedf85c840f57a7b57d082ab1dece4375b71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="27cd2-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="27cd2-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="27cd2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="27cd2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27cd2-104">ID</span><span class="sxs-lookup"><span data-stu-id="27cd2-104">ID</span></span>|<span data-ttu-id="27cd2-105">4202</span><span class="sxs-lookup"><span data-stu-id="27cd2-105">4202</span></span>|  
|<span data-ttu-id="27cd2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="27cd2-106">Keywords</span></span>|<span data-ttu-id="27cd2-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="27cd2-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="27cd2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="27cd2-108">Level</span></span>|<span data-ttu-id="27cd2-109">詳細</span><span class="sxs-lookup"><span data-stu-id="27cd2-109">Verbose</span></span>|  
|<span data-ttu-id="27cd2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="27cd2-110">Channel</span></span>|<span data-ttu-id="27cd2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="27cd2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="27cd2-112">説明</span><span class="sxs-lookup"><span data-stu-id="27cd2-112">Description</span></span>  
 <span data-ttu-id="27cd2-113">SQL コマンドが実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="27cd2-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="27cd2-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="27cd2-114">Message</span></span>  
 <span data-ttu-id="27cd2-115">SQL コマンドの実行を開始します: %1</span><span class="sxs-lookup"><span data-stu-id="27cd2-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="27cd2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="27cd2-116">Details</span></span>  
  
|<span data-ttu-id="27cd2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="27cd2-117">Data Item Name</span></span>|<span data-ttu-id="27cd2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="27cd2-118">Data Item Type</span></span>|<span data-ttu-id="27cd2-119">説明</span><span class="sxs-lookup"><span data-stu-id="27cd2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="27cd2-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="27cd2-120">SqlCommand</span></span>|<span data-ttu-id="27cd2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="27cd2-121">xs:string</span></span>|<span data-ttu-id="27cd2-122">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="27cd2-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="27cd2-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="27cd2-123">AppDomain</span></span>|<span data-ttu-id="27cd2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="27cd2-124">xs:string</span></span>|<span data-ttu-id="27cd2-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="27cd2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
