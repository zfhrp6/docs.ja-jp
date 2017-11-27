---
title: "サービス : 1 秒あたりのセキュリティ検証と認証エラー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 007bc3b38ef5b635a85e4c13f9bc9a6424fc36ad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="0b5e9-102">サービス : 1 秒あたりのセキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="0b5e9-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="0b5e9-103">カウンター名 : 1 秒あたりのセキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="0b5e9-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0b5e9-104">説明</span><span class="sxs-lookup"><span data-stu-id="0b5e9-104">Description</span></span>  
 <span data-ttu-id="0b5e9-105">このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="0b5e9-106">この問題には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="0b5e9-107">メッセージからクライアント トークンを読み取ることができない。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="0b5e9-108">クライアント トークンが認証に失敗した (例 : 無効なパスワード)。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="0b5e9-109">署名の検証に失敗した (例 : メッセージが改ざんされた)。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="0b5e9-110">メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="0b5e9-111">復号化に失敗した。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="0b5e9-112">一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="0b5e9-113">TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="0b5e9-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="0b5e9-114">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、その値は、次の式を使用して計算</span><span class="sxs-lookup"><span data-stu-id="0b5e9-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="0b5e9-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0b5e9-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
