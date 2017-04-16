---
title: "WS-AtomicTransaction の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WS-AT プロトコル [WCF]"
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# WS-AtomicTransaction の使用
WS\-AtomicTransaction \(WS\-AT\) は、相互運用が可能なトランザクション プロトコルです。Web サービス メッセージを使用して分散トランザクションをフローできるようにすると共に、異種のトランザクション インフラストラクチャ間で相互運用できるように調整します。WS\-AT では、2 フェーズ コミット プロトコルを使用して、分散アプリケーション、トランザクション マネージャー、およびリソース マネージャー間でアトミックな結果を実現します。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で提供される WS\-AT 実装には、Microsoft 分散トランザクション コーディネーター \(MSDTC\) トランザクション マネージャーに組み込まれたプロトコル サービスが含まれています。WS\-AT を使用することにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、サードパーティのテクノロジを使用して構築された相互運用可能な Web サービスを含む、他のアプリケーションにトランザクションをフローさせることができます。  
  
 クライアント アプリケーションとサーバー アプリケーション間でトランザクションをフローさせるときに使用されるトランザクション プロトコルは、クライアントが選択したエンドポイントでサーバーが公開するバインディングによって決定されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] システム指定のバインディングでは、トランザクションの伝達形式として既定で `OleTransactions` プロトコルを指定するものと、WS\-AT を指定するものがあります。特定のバインディング内部でのトランザクション プロトコルの選択は、プログラムによって変更することもできます。  
  
 プロトコルの選択は、次の内容に影響を与えます。  
  
-   トランザクションをクライアントからサーバーにフローさせるために使用されるメッセージ ヘッダーの形式。  
  
-   トランザクションの結果を解決するために、クライアントのトランザクション マネージャーとサーバーのトランザクション マネージャーの間で 2 フェーズ コミット プロトコルを実行するために使用されるネットワーク プロトコル。  
  
 サーバーとクライアントが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して記述されている場合、WS\-AT を使用する必要はありません。その代わりに、`OleTransactions` プロトコルを使用する `TransactionFlow` 属性を有効にして `NetTcpBinding` の既定の設定を使用できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).ただし、サード パーティのテクノロジで構築された Web サービスにトランザクションをフローさせる場合は、WS\-AT を使用する必要があります。  
  
## 参照  
 [WS\-AtomicTransaction サポートの構成](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)