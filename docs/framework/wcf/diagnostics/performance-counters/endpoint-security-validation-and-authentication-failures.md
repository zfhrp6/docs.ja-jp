---
title: "エンドポイント : セキュリティ検証エラーと認証エラー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# エンドポイント : セキュリティ検証エラーと認証エラー
カウンター名 : セキュリティ検証と認証エラー  
  
## 説明  
 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびに増分されます。この問題には、次のようなものがあります。  
  
-   メッセージからクライアント トークンを読み取ることができない。  
  
-   クライアント トークンが認証に失敗した \(無効なパスワード\)。  
  
-   署名の検証に失敗した \(メッセージが改変された\)。  
  
-   メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
-   復号化に失敗した。  
  
-   一部の必須要素 \(タイムスタンプ、暗号化データ ブロック\) がメッセージにない。  
  
-   TLSNEGO\/SPNEGO ハンドシェイク中にエラーが発生した。