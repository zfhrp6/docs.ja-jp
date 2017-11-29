---
title: 4201 - EndSqlCommandExecute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57c413ddae884f50e8f65eac146ccf5b2fc84b8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="d188c-102">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="d188c-102">4201 - EndSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="d188c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d188c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d188c-104">ID</span><span class="sxs-lookup"><span data-stu-id="d188c-104">ID</span></span>|<span data-ttu-id="d188c-105">4201</span><span class="sxs-lookup"><span data-stu-id="d188c-105">4201</span></span>|  
|<span data-ttu-id="d188c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d188c-106">Keywords</span></span>|<span data-ttu-id="d188c-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d188c-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d188c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d188c-108">Level</span></span>|<span data-ttu-id="d188c-109">詳細</span><span class="sxs-lookup"><span data-stu-id="d188c-109">Verbose</span></span>|  
|<span data-ttu-id="d188c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d188c-110">Channel</span></span>|<span data-ttu-id="d188c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d188c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d188c-112">説明</span><span class="sxs-lookup"><span data-stu-id="d188c-112">Description</span></span>  
 <span data-ttu-id="d188c-113">SQL コマンドの実行が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d188c-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d188c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d188c-114">Message</span></span>  
 <span data-ttu-id="d188c-115">SQL コマンドの実行を終了します: %1</span><span class="sxs-lookup"><span data-stu-id="d188c-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="d188c-116">詳細</span><span class="sxs-lookup"><span data-stu-id="d188c-116">Details</span></span>  
  
|<span data-ttu-id="d188c-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d188c-117">Data Item Name</span></span>|<span data-ttu-id="d188c-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d188c-118">Data Item Type</span></span>|<span data-ttu-id="d188c-119">説明</span><span class="sxs-lookup"><span data-stu-id="d188c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d188c-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="d188c-120">SqlCommand</span></span>|<span data-ttu-id="d188c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d188c-121">xs:string</span></span>|<span data-ttu-id="d188c-122">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="d188c-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="d188c-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d188c-123">AppDomain</span></span>|<span data-ttu-id="d188c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d188c-124">xs:string</span></span>|<span data-ttu-id="d188c-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d188c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
