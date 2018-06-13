---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: b763e087d8ead2bcc0fadd1d0223ae1bd58c9fd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511460"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="12048-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="12048-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="12048-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="12048-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12048-104">ID</span><span class="sxs-lookup"><span data-stu-id="12048-104">ID</span></span>|<span data-ttu-id="12048-105">4207</span><span class="sxs-lookup"><span data-stu-id="12048-105">4207</span></span>|  
|<span data-ttu-id="12048-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="12048-106">Keywords</span></span>|<span data-ttu-id="12048-107">クオータ、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="12048-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="12048-108">レベル</span><span class="sxs-lookup"><span data-stu-id="12048-108">Level</span></span>|<span data-ttu-id="12048-109">情報</span><span class="sxs-lookup"><span data-stu-id="12048-109">Information</span></span>|  
|<span data-ttu-id="12048-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="12048-110">Channel</span></span>|<span data-ttu-id="12048-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="12048-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="12048-112">説明</span><span class="sxs-lookup"><span data-stu-id="12048-112">Description</span></span>  
 <span data-ttu-id="12048-113">再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="12048-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="12048-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="12048-114">Message</span></span>  
 <span data-ttu-id="12048-115">SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="12048-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="12048-116">詳細</span><span class="sxs-lookup"><span data-stu-id="12048-116">Details</span></span>  
  
|<span data-ttu-id="12048-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="12048-117">Data Item Name</span></span>|<span data-ttu-id="12048-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="12048-118">Data Item Type</span></span>|<span data-ttu-id="12048-119">説明</span><span class="sxs-lookup"><span data-stu-id="12048-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="12048-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="12048-120">AppDomain</span></span>|<span data-ttu-id="12048-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="12048-121">xs:string</span></span>|<span data-ttu-id="12048-122">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="12048-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
