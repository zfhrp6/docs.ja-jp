---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474169"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="e1c28-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="e1c28-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="e1c28-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e1c28-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1c28-104">ID</span><span class="sxs-lookup"><span data-stu-id="e1c28-104">ID</span></span>|<span data-ttu-id="e1c28-105">401</span><span class="sxs-lookup"><span data-stu-id="e1c28-105">401</span></span>|  
|<span data-ttu-id="e1c28-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e1c28-106">Keywords</span></span>|<span data-ttu-id="e1c28-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e1c28-107">Troubleshooting</span></span>|  
|<span data-ttu-id="e1c28-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e1c28-108">Level</span></span>|<span data-ttu-id="e1c28-109">情報</span><span class="sxs-lookup"><span data-stu-id="e1c28-109">Information</span></span>|  
|<span data-ttu-id="e1c28-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e1c28-110">Channel</span></span>|<span data-ttu-id="e1c28-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e1c28-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1c28-112">説明</span><span class="sxs-lookup"><span data-stu-id="e1c28-112">Description</span></span>  
 <span data-ttu-id="e1c28-113">このイベントは、エンド ツー エンド アクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="e1c28-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="e1c28-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="e1c28-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1c28-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e1c28-115">Message</span></span>  
 <span data-ttu-id="e1c28-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="e1c28-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1c28-117">詳細</span><span class="sxs-lookup"><span data-stu-id="e1c28-117">Details</span></span>  
  
|<span data-ttu-id="e1c28-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e1c28-118">Data Item Name</span></span>|<span data-ttu-id="e1c28-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e1c28-119">Data Item Type</span></span>|<span data-ttu-id="e1c28-120">説明</span><span class="sxs-lookup"><span data-stu-id="e1c28-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1c28-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="e1c28-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="e1c28-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="e1c28-122">The name of the activity.</span></span>|  
|<span data-ttu-id="e1c28-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1c28-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e1c28-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e1c28-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
