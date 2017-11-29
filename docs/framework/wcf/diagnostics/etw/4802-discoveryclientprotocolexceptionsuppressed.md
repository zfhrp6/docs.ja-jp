---
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce1371df6015f6f6faa48ba2a1cddabf2ef12a5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="61bbd-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="61bbd-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>
## <a name="properties"></a><span data-ttu-id="61bbd-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="61bbd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61bbd-104">ID</span><span class="sxs-lookup"><span data-stu-id="61bbd-104">ID</span></span>|<span data-ttu-id="61bbd-105">4802</span><span class="sxs-lookup"><span data-stu-id="61bbd-105">4802</span></span>|  
|<span data-ttu-id="61bbd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="61bbd-106">Keywords</span></span>|<span data-ttu-id="61bbd-107">探索</span><span class="sxs-lookup"><span data-stu-id="61bbd-107">Discovery</span></span>|  
|<span data-ttu-id="61bbd-108">レベル</span><span class="sxs-lookup"><span data-stu-id="61bbd-108">Level</span></span>|<span data-ttu-id="61bbd-109">情報</span><span class="sxs-lookup"><span data-stu-id="61bbd-109">Information</span></span>|  
|<span data-ttu-id="61bbd-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="61bbd-110">Channel</span></span>|<span data-ttu-id="61bbd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="61bbd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="61bbd-112">説明</span><span class="sxs-lookup"><span data-stu-id="61bbd-112">Description</span></span>  
 <span data-ttu-id="61bbd-113">このイベントは DiscoveryClient の終了中に ProtocolException が抑制されたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="61bbd-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="61bbd-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="61bbd-114">Message</span></span>  
 <span data-ttu-id="61bbd-115">DiscoveryClient を閉じているときに ProtocolException が抑制されました。</span><span class="sxs-lookup"><span data-stu-id="61bbd-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="61bbd-116">その理由として、DiscoveryService がまだ DiscoveryClient に応答を送信しようとしていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="61bbd-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="61bbd-117">詳細</span><span class="sxs-lookup"><span data-stu-id="61bbd-117">Details</span></span>
