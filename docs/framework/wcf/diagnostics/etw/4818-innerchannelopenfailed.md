---
title: 4818 - InnerChannelOpenFailed
ms.date: 03/30/2017
ms.assetid: c8ac6447-4fbb-4e08-ab26-91acae48dd11
ms.openlocfilehash: e98d76b21513d409250cd621003c583e33f980c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="4818---innerchannelopenfailed"></a><span data-ttu-id="341aa-102">4818 - InnerChannelOpenFailed</span><span class="sxs-lookup"><span data-stu-id="341aa-102">4818 - InnerChannelOpenFailed</span></span>
## <a name="properties"></a><span data-ttu-id="341aa-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="341aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="341aa-104">ID</span><span class="sxs-lookup"><span data-stu-id="341aa-104">ID</span></span>|<span data-ttu-id="341aa-105">4818</span><span class="sxs-lookup"><span data-stu-id="341aa-105">4818</span></span>|  
|<span data-ttu-id="341aa-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="341aa-106">Keywords</span></span>|<span data-ttu-id="341aa-107">探索</span><span class="sxs-lookup"><span data-stu-id="341aa-107">Discovery</span></span>|  
|<span data-ttu-id="341aa-108">レベル</span><span class="sxs-lookup"><span data-stu-id="341aa-108">Level</span></span>|<span data-ttu-id="341aa-109">警告</span><span class="sxs-lookup"><span data-stu-id="341aa-109">Warning</span></span>|  
|<span data-ttu-id="341aa-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="341aa-110">Channel</span></span>|<span data-ttu-id="341aa-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="341aa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="341aa-112">説明</span><span class="sxs-lookup"><span data-stu-id="341aa-112">Description</span></span>  
 <span data-ttu-id="341aa-113">このイベントは、DiscoveryClientChannel が、探索されたエンドポイントを使用してチャネルを開くことができなかったときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="341aa-113">This event is emitted when the DiscoveryClientChannel failed to open the channel with a discovered endpoint.</span></span> <span data-ttu-id="341aa-114">DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="341aa-114">The DiscoveryClientChannel will now attempt to use the next available discovered endpoint.</span></span>  
  
## <a name="message"></a><span data-ttu-id="341aa-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="341aa-115">Message</span></span>  
 <span data-ttu-id="341aa-116">DiscoveryClientChannel は、EndpointAddress='%1' および Via='%2' の探索されたエンドポイントを使用して、チャネルを開くことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="341aa-116">The DiscoveryClientChannel failed to open the channel with a discovered endpoint with EndpointAddress='%1' and Via='%2'.</span></span> <span data-ttu-id="341aa-117">DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="341aa-117">The DiscoveryClientChannel will now attempt to use the next available discovered endpoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="341aa-118">詳細</span><span class="sxs-lookup"><span data-stu-id="341aa-118">Details</span></span>
