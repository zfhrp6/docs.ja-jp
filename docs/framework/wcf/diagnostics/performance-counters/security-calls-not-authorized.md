---
title: 承認されていないセキュリティ呼び出し
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3554644a7f73894703cc26ad11e4f7b9d58cab60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472574"
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="949d1-102">承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="949d1-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="949d1-103">カウンター名 : 承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="949d1-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="949d1-104">説明</span><span class="sxs-lookup"><span data-stu-id="949d1-104">Description</span></span>  
 <span data-ttu-id="949d1-105">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="949d1-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="949d1-106">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="949d1-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
