---
title: 'エンドポイント : 承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b449aaad65f01a5f4835f8335543220383543984
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471257"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="9891f-102">エンドポイント : 承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="9891f-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="9891f-103">カウンター名 : 承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="9891f-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9891f-104">説明</span><span class="sxs-lookup"><span data-stu-id="9891f-104">Description</span></span>  
 <span data-ttu-id="9891f-105">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="9891f-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="9891f-106">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9891f-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
