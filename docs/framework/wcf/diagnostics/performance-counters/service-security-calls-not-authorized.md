---
title: 'サービス : 承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: eb0f0d3e3005a4efca27ec3a63e2a854f735258b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472204"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="ac852-102">サービス : 承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="ac852-102">Service: Security Calls Not Authorized</span></span>
<span data-ttu-id="ac852-103">カウンター名 : 承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ac852-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ac852-104">説明</span><span class="sxs-lookup"><span data-stu-id="ac852-104">Description</span></span>  
 <span data-ttu-id="ac852-105">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="ac852-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="ac852-106">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ac852-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
