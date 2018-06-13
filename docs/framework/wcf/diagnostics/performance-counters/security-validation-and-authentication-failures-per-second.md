---
title: 1 秒あたりのセキュリティ検証と認証エラー
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e69dafaf2e415a0686594c4757bcf20dfd135944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473231"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="ab6b9-102">1 秒あたりのセキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="ab6b9-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="ab6b9-103">カウンター名 : 1 秒あたりのセキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="ab6b9-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ab6b9-104">説明</span><span class="sxs-lookup"><span data-stu-id="ab6b9-104">Description</span></span>  
 <span data-ttu-id="ab6b9-105">このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="ab6b9-106">この問題には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="ab6b9-107">メッセージからクライアント トークンを読み取ることができない。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="ab6b9-108">クライアント トークンが認証に失敗した (例 : 無効なパスワード)。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="ab6b9-109">署名の検証に失敗した (例 : メッセージが改ざんされた)。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="ab6b9-110">メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="ab6b9-111">復号化に失敗した。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="ab6b9-112">一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="ab6b9-113">TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="ab6b9-114">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="ab6b9-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="ab6b9-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="ab6b9-115">(N1-N0)/((D1-D0)/F)</span></span>
