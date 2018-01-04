---
title: "セキュリティ検証と認証エラー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c52b54d2be2e824de478e0ee9ec2452c57e181b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="d9c75-102">セキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="d9c75-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="d9c75-103">カウンター名 : セキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="d9c75-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="d9c75-104">説明</span><span class="sxs-lookup"><span data-stu-id="d9c75-104">Description</span></span>  
 <span data-ttu-id="d9c75-105">このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="d9c75-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="d9c75-106">この問題には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="d9c75-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="d9c75-107">メッセージからクライアント トークンを読み取ることができない。</span><span class="sxs-lookup"><span data-stu-id="d9c75-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="d9c75-108">クライアント トークンが認証に失敗した (例 : 無効なパスワード)。</span><span class="sxs-lookup"><span data-stu-id="d9c75-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="d9c75-109">署名の検証に失敗した (例 : メッセージが改ざんされた)。</span><span class="sxs-lookup"><span data-stu-id="d9c75-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="d9c75-110">メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d9c75-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="d9c75-111">復号化に失敗した。</span><span class="sxs-lookup"><span data-stu-id="d9c75-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="d9c75-112">一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。</span><span class="sxs-lookup"><span data-stu-id="d9c75-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="d9c75-113">TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="d9c75-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
