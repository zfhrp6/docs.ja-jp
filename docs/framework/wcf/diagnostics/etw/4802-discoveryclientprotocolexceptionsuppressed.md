---
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.date: 03/30/2017
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
ms.openlocfilehash: 5bb7772d668a6b635130c899ada9879c9c1f69a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33468206"
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="7992c-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="7992c-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>
## <a name="properties"></a><span data-ttu-id="7992c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7992c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7992c-104">ID</span><span class="sxs-lookup"><span data-stu-id="7992c-104">ID</span></span>|<span data-ttu-id="7992c-105">4802</span><span class="sxs-lookup"><span data-stu-id="7992c-105">4802</span></span>|  
|<span data-ttu-id="7992c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7992c-106">Keywords</span></span>|<span data-ttu-id="7992c-107">探索</span><span class="sxs-lookup"><span data-stu-id="7992c-107">Discovery</span></span>|  
|<span data-ttu-id="7992c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7992c-108">Level</span></span>|<span data-ttu-id="7992c-109">情報</span><span class="sxs-lookup"><span data-stu-id="7992c-109">Information</span></span>|  
|<span data-ttu-id="7992c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7992c-110">Channel</span></span>|<span data-ttu-id="7992c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7992c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7992c-112">説明</span><span class="sxs-lookup"><span data-stu-id="7992c-112">Description</span></span>  
 <span data-ttu-id="7992c-113">このイベントは DiscoveryClient の終了中に ProtocolException が抑制されたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="7992c-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7992c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7992c-114">Message</span></span>  
 <span data-ttu-id="7992c-115">DiscoveryClient を閉じているときに ProtocolException が抑制されました。</span><span class="sxs-lookup"><span data-stu-id="7992c-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="7992c-116">その理由として、DiscoveryService がまだ DiscoveryClient に応答を送信しようとしていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="7992c-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7992c-117">詳細</span><span class="sxs-lookup"><span data-stu-id="7992c-117">Details</span></span>
