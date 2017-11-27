---
title: 401- StopSignPostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 31cd94e2c988d614babc1e0c203316b41e01f5bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="d03ff-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="d03ff-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="d03ff-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d03ff-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d03ff-104">ID</span><span class="sxs-lookup"><span data-stu-id="d03ff-104">ID</span></span>|<span data-ttu-id="d03ff-105">401</span><span class="sxs-lookup"><span data-stu-id="d03ff-105">401</span></span>|  
|<span data-ttu-id="d03ff-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d03ff-106">Keywords</span></span>|<span data-ttu-id="d03ff-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d03ff-107">Troubleshooting</span></span>|  
|<span data-ttu-id="d03ff-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d03ff-108">Level</span></span>|<span data-ttu-id="d03ff-109">情報</span><span class="sxs-lookup"><span data-stu-id="d03ff-109">Information</span></span>|  
|<span data-ttu-id="d03ff-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d03ff-110">Channel</span></span>|<span data-ttu-id="d03ff-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d03ff-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d03ff-112">説明</span><span class="sxs-lookup"><span data-stu-id="d03ff-112">Description</span></span>  
 <span data-ttu-id="d03ff-113">このイベントは、エンド ツー エンド アクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="d03ff-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="d03ff-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="d03ff-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d03ff-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d03ff-115">Message</span></span>  
 <span data-ttu-id="d03ff-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="d03ff-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d03ff-117">詳細</span><span class="sxs-lookup"><span data-stu-id="d03ff-117">Details</span></span>  
  
|<span data-ttu-id="d03ff-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d03ff-118">Data Item Name</span></span>|<span data-ttu-id="d03ff-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d03ff-119">Data Item Type</span></span>|<span data-ttu-id="d03ff-120">説明</span><span class="sxs-lookup"><span data-stu-id="d03ff-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d03ff-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="d03ff-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="d03ff-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="d03ff-122">The name of the activity.</span></span>|  
|<span data-ttu-id="d03ff-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d03ff-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d03ff-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d03ff-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
