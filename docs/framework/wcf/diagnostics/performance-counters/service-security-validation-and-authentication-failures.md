---
title: "サービス : セキュリティ検証と認証エラー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 50944c55525150868e5ddac9730792c10f6b975c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service-security-validation-and-authentication-failures"></a>サービス : セキュリティ検証と認証エラー
カウンター名 : セキュリティ検証と認証エラー  
  
## <a name="description"></a>説明  
 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。 この問題には、次のようなものがあります。  
  
-   メッセージからクライアント トークンを読み取ることができない。  
  
-   クライアント トークンが認証に失敗した (例 : 無効なパスワード)。  
  
-   署名の検証に失敗した (例 : メッセージが改ざんされた)。  
  
-   メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
-   復号化に失敗した。  
  
-   一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。  
  
-   TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。
