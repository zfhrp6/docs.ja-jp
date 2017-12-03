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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d54660ed7f278b1f82fac81c31b8a30e20a2e7d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="32289-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="32289-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="32289-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="32289-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32289-104">ID</span><span class="sxs-lookup"><span data-stu-id="32289-104">ID</span></span>|<span data-ttu-id="32289-105">4202</span><span class="sxs-lookup"><span data-stu-id="32289-105">4202</span></span>|  
|<span data-ttu-id="32289-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="32289-106">Keywords</span></span>|<span data-ttu-id="32289-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="32289-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="32289-108">レベル</span><span class="sxs-lookup"><span data-stu-id="32289-108">Level</span></span>|<span data-ttu-id="32289-109">詳細</span><span class="sxs-lookup"><span data-stu-id="32289-109">Verbose</span></span>|  
|<span data-ttu-id="32289-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="32289-110">Channel</span></span>|<span data-ttu-id="32289-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="32289-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32289-112">説明</span><span class="sxs-lookup"><span data-stu-id="32289-112">Description</span></span>  
 <span data-ttu-id="32289-113">SQL コマンドが実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="32289-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32289-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="32289-114">Message</span></span>  
 <span data-ttu-id="32289-115">SQL コマンドの実行を開始します: %1</span><span class="sxs-lookup"><span data-stu-id="32289-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="32289-116">詳細</span><span class="sxs-lookup"><span data-stu-id="32289-116">Details</span></span>  
  
|<span data-ttu-id="32289-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="32289-117">Data Item Name</span></span>|<span data-ttu-id="32289-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="32289-118">Data Item Type</span></span>|<span data-ttu-id="32289-119">説明</span><span class="sxs-lookup"><span data-stu-id="32289-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32289-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="32289-120">SqlCommand</span></span>|<span data-ttu-id="32289-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="32289-121">xs:string</span></span>|<span data-ttu-id="32289-122">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="32289-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="32289-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="32289-123">AppDomain</span></span>|<span data-ttu-id="32289-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="32289-124">xs:string</span></span>|<span data-ttu-id="32289-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="32289-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
