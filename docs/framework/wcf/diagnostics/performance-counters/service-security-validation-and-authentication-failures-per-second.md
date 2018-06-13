---
title: 'サービス : 1 秒あたりのセキュリティ検証と認証エラー'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0dadf11888e55a96b15e09d5f4b326e8c5e18a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474819"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a>サービス : 1 秒あたりのセキュリティ検証と認証エラー
カウンター名 : 1 秒あたりのセキュリティ検証と認証エラー  
  
## <a name="description"></a>説明  
 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。 この問題には、次のようなものがあります。  
  
-   メッセージからクライアント トークンを読み取ることができない。  
  
-   クライアント トークンが認証に失敗した (例 : 無効なパスワード)。  
  
-   署名の検証に失敗した (例 : メッセージが改ざんされた)。  
  
-   メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
-   復号化に失敗した。  
  
-   一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。  
  
-   TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、その値は、次の式を使用して計算  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
