---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510352"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="0bf94-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="0bf94-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="0bf94-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0bf94-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0bf94-104">ID</span><span class="sxs-lookup"><span data-stu-id="0bf94-104">ID</span></span>|<span data-ttu-id="0bf94-105">4202</span><span class="sxs-lookup"><span data-stu-id="0bf94-105">4202</span></span>|  
|<span data-ttu-id="0bf94-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="0bf94-106">Keywords</span></span>|<span data-ttu-id="0bf94-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0bf94-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0bf94-108">レベル</span><span class="sxs-lookup"><span data-stu-id="0bf94-108">Level</span></span>|<span data-ttu-id="0bf94-109">詳細</span><span class="sxs-lookup"><span data-stu-id="0bf94-109">Verbose</span></span>|  
|<span data-ttu-id="0bf94-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0bf94-110">Channel</span></span>|<span data-ttu-id="0bf94-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0bf94-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0bf94-112">説明</span><span class="sxs-lookup"><span data-stu-id="0bf94-112">Description</span></span>  
 <span data-ttu-id="0bf94-113">SQL コマンドが実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="0bf94-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0bf94-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="0bf94-114">Message</span></span>  
 <span data-ttu-id="0bf94-115">SQL コマンドの実行を開始します: %1</span><span class="sxs-lookup"><span data-stu-id="0bf94-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="0bf94-116">詳細</span><span class="sxs-lookup"><span data-stu-id="0bf94-116">Details</span></span>  
  
|<span data-ttu-id="0bf94-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0bf94-117">Data Item Name</span></span>|<span data-ttu-id="0bf94-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0bf94-118">Data Item Type</span></span>|<span data-ttu-id="0bf94-119">説明</span><span class="sxs-lookup"><span data-stu-id="0bf94-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0bf94-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="0bf94-120">SqlCommand</span></span>|<span data-ttu-id="0bf94-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0bf94-121">xs:string</span></span>|<span data-ttu-id="0bf94-122">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="0bf94-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="0bf94-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0bf94-123">AppDomain</span></span>|<span data-ttu-id="0bf94-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0bf94-124">xs:string</span></span>|<span data-ttu-id="0bf94-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0bf94-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
