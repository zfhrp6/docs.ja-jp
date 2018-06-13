---
title: 1 秒あたりの承認されていないセキュリティ呼び出し
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f04abc46a85f151108653b399c238e0275bf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473556"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="649da-102">1 秒あたりの承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="649da-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="649da-103">カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="649da-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="649da-104">説明</span><span class="sxs-lookup"><span data-stu-id="649da-104">Description</span></span>  
 <span data-ttu-id="649da-105">この操作で 1 秒あたりに承認に失敗した呼び出しの数です。</span><span class="sxs-lookup"><span data-stu-id="649da-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="649da-106">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="649da-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="649da-107">受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="649da-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="649da-108">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="649da-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="649da-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="649da-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
