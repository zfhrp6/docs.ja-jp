---
title: 440 - StartSignpostEvent1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6cc59e1394c33321d74b9f48dd4a78af204ae31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="440---startsignpostevent1"></a><span data-ttu-id="2149b-102">440 - StartSignpostEvent1</span><span class="sxs-lookup"><span data-stu-id="2149b-102">440 - StartSignpostEvent1</span></span>
## <a name="properties"></a><span data-ttu-id="2149b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2149b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2149b-104">ID</span><span class="sxs-lookup"><span data-stu-id="2149b-104">ID</span></span>|<span data-ttu-id="2149b-105">440</span><span class="sxs-lookup"><span data-stu-id="2149b-105">440</span></span>|  
|<span data-ttu-id="2149b-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2149b-106">Keywords</span></span>|<span data-ttu-id="2149b-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2149b-107">Troubleshooting</span></span>|  
|<span data-ttu-id="2149b-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2149b-108">Level</span></span>|<span data-ttu-id="2149b-109">情報</span><span class="sxs-lookup"><span data-stu-id="2149b-109">Information</span></span>|  
|<span data-ttu-id="2149b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2149b-110">Channel</span></span>|<span data-ttu-id="2149b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2149b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2149b-112">説明</span><span class="sxs-lookup"><span data-stu-id="2149b-112">Description</span></span>  
 <span data-ttu-id="2149b-113">アクティビティ トレースでは、送信または受信においてメッセージがアクティビティの境界を越え始めたことを示します。</span><span class="sxs-lookup"><span data-stu-id="2149b-113">In activity tracing, indicates a message has started crossing an activity boundary in send or receive.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2149b-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2149b-114">Message</span></span>  
 <span data-ttu-id="2149b-115">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="2149b-115">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2149b-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2149b-116">Details</span></span>  
  
|<span data-ttu-id="2149b-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2149b-117">Data Item Name</span></span>|<span data-ttu-id="2149b-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2149b-118">Data Item Type</span></span>|<span data-ttu-id="2149b-119">説明</span><span class="sxs-lookup"><span data-stu-id="2149b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2149b-120">ExtendedData</span><span class="sxs-lookup"><span data-stu-id="2149b-120">ExtendedData</span></span>|`xs:string`|<span data-ttu-id="2149b-121">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="2149b-121">The name of the activity.</span></span>|  
|<span data-ttu-id="2149b-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2149b-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2149b-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2149b-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
