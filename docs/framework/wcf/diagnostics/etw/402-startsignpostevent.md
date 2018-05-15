---
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: 6dfb3b187f58de2c9573c2d2f6d579e3557c3de8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="d7679-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="d7679-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="d7679-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d7679-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7679-104">ID</span><span class="sxs-lookup"><span data-stu-id="d7679-104">ID</span></span>|<span data-ttu-id="d7679-105">402</span><span class="sxs-lookup"><span data-stu-id="d7679-105">402</span></span>|  
|<span data-ttu-id="d7679-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d7679-106">Keywords</span></span>|<span data-ttu-id="d7679-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d7679-107">Troubleshooting</span></span>|  
|<span data-ttu-id="d7679-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d7679-108">Level</span></span>|<span data-ttu-id="d7679-109">情報</span><span class="sxs-lookup"><span data-stu-id="d7679-109">Information</span></span>|  
|<span data-ttu-id="d7679-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d7679-110">Channel</span></span>|<span data-ttu-id="d7679-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d7679-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d7679-112">説明</span><span class="sxs-lookup"><span data-stu-id="d7679-112">Description</span></span>  
 <span data-ttu-id="d7679-113">このイベントは、エンド ツー エンド アクティビティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="d7679-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="d7679-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="d7679-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d7679-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d7679-115">Message</span></span>  
 <span data-ttu-id="d7679-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="d7679-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d7679-117">詳細</span><span class="sxs-lookup"><span data-stu-id="d7679-117">Details</span></span>  
  
|<span data-ttu-id="d7679-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d7679-118">Data Item Name</span></span>|<span data-ttu-id="d7679-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d7679-119">Data Item Type</span></span>|<span data-ttu-id="d7679-120">説明</span><span class="sxs-lookup"><span data-stu-id="d7679-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d7679-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="d7679-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="d7679-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="d7679-122">The name of the activity.</span></span>|  
|<span data-ttu-id="d7679-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d7679-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d7679-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d7679-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
