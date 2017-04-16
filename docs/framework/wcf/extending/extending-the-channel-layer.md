---
title: "チャネル レイヤーの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "チャネルの拡張 [WCF]"
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# チャネル レイヤーの拡張
チャネル レイヤーはクライアントとサービス間のメッセージの交換を担います。チャネル拡張では、新しいプロトコル機能 \(セキュリティなど\)、またはトランスポート機能 \(SOAP メッセージを送信する新しいネットワーク トランスポートの実装など\) を実装できます。  
  
## このセクションの内容  
 [チャネル モデルの概要](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 チャネルとその機能、サービス アプリケーションおよびクライアント アプリケーションとの連携について概要を示します。  
  
 [チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)  
 各種のチャネル インフラストラクチャが果たす役割、ステート エンジンとステート ライフサイクルのしくみ、例外とエラーの処理方法、メタデータ サポートの実装方法、チャネルとメッセージ エンコーダーの連携について詳しく説明します。  
  
 [カスタム エンコーダー](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 メッセージ エンコーダーがチャネルで果たす役割、およびメッセージ エンコーダーの作成方法について説明します。  
  
 [カスタム ストリームのアップグレード](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 ストリーム指向のトランスポートによって提供されるストリームのアップグレード プロセスについて説明します。