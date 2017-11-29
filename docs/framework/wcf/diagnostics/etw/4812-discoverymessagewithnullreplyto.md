---
title: 4812 - DiscoveryMessageWithNullReplyTo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a40e6b7e-c2a6-4186-b1d6-c9560f24a959
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dad079e4cd2a781d9a8fe7dea388f44400549a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4812---discoverymessagewithnullreplyto"></a><span data-ttu-id="8c748-102">4812 - DiscoveryMessageWithNullReplyTo</span><span class="sxs-lookup"><span data-stu-id="8c748-102">4812 - DiscoveryMessageWithNullReplyTo</span></span>
## <a name="properties"></a><span data-ttu-id="8c748-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c748-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c748-104">ID</span><span class="sxs-lookup"><span data-stu-id="8c748-104">ID</span></span>|<span data-ttu-id="8c748-105">4812</span><span class="sxs-lookup"><span data-stu-id="8c748-105">4812</span></span>|  
|<span data-ttu-id="8c748-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="8c748-106">Keywords</span></span>|<span data-ttu-id="8c748-107">探索</span><span class="sxs-lookup"><span data-stu-id="8c748-107">Discovery</span></span>|  
|<span data-ttu-id="8c748-108">レベル</span><span class="sxs-lookup"><span data-stu-id="8c748-108">Level</span></span>|<span data-ttu-id="8c748-109">警告</span><span class="sxs-lookup"><span data-stu-id="8c748-109">Warning</span></span>|  
|<span data-ttu-id="8c748-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8c748-110">Channel</span></span>|<span data-ttu-id="8c748-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8c748-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c748-112">説明</span><span class="sxs-lookup"><span data-stu-id="8c748-112">Description</span></span>  
 <span data-ttu-id="8c748-113">このイベントは、ReplyTo アドレスがなかったことが原因で探索要求メッセージが DiscoveryClient によってドロップされたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="8c748-113">This event is emitted when the discovery message was dropped by the DiscoveryClient because it did not have a ReplyTo address.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c748-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="8c748-114">Message</span></span>  
 <span data-ttu-id="8c748-115">messageId='%1' の探索要求メッセージは、ReplyTo アドレスがなかったため、ドロップされました。</span><span class="sxs-lookup"><span data-stu-id="8c748-115">A discovery request message with messageId='%1' was dropped because it did not have a ReplyTo address.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c748-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8c748-116">Details</span></span>
