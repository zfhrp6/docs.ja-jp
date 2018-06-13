---
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 3c981888b491f2797a431c2103ba3f5f0bd17046
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511174"
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="57636-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="57636-102">4206 - UnlockInstanceException</span></span>
## <a name="properties"></a><span data-ttu-id="57636-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="57636-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57636-104">ID</span><span class="sxs-lookup"><span data-stu-id="57636-104">ID</span></span>|<span data-ttu-id="57636-105">4206</span><span class="sxs-lookup"><span data-stu-id="57636-105">4206</span></span>|  
|<span data-ttu-id="57636-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="57636-106">Keywords</span></span>|<span data-ttu-id="57636-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="57636-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="57636-108">レベル</span><span class="sxs-lookup"><span data-stu-id="57636-108">Level</span></span>|<span data-ttu-id="57636-109">Error</span><span class="sxs-lookup"><span data-stu-id="57636-109">Error</span></span>|  
|<span data-ttu-id="57636-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="57636-110">Channel</span></span>|<span data-ttu-id="57636-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="57636-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57636-112">説明</span><span class="sxs-lookup"><span data-stu-id="57636-112">Description</span></span>  
 <span data-ttu-id="57636-113">インスタンスのロックを解除しようとしているときに例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="57636-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57636-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="57636-114">Message</span></span>  
 <span data-ttu-id="57636-115">インスタンスのロックを解除しようとして、例外 %1 が発生しました。</span><span class="sxs-lookup"><span data-stu-id="57636-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57636-116">詳細</span><span class="sxs-lookup"><span data-stu-id="57636-116">Details</span></span>  
  
|<span data-ttu-id="57636-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="57636-117">Data Item Name</span></span>|<span data-ttu-id="57636-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="57636-118">Data Item Type</span></span>|<span data-ttu-id="57636-119">説明</span><span class="sxs-lookup"><span data-stu-id="57636-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57636-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="57636-120">ExceptionMessage</span></span>|<span data-ttu-id="57636-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="57636-121">xs:string</span></span>|<span data-ttu-id="57636-122">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="57636-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="57636-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="57636-123">AppDomain</span></span>|<span data-ttu-id="57636-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="57636-124">xs:string</span></span>|<span data-ttu-id="57636-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="57636-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
