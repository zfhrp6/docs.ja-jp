---
title: "ルーティング コントラクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# ルーティング コントラクト
ルーティング コントラクトは、ルーティング サービスが処理できるメッセージ パターンを定義します。各コントラクトは型指定されておらず、サービスは、メッセージ スキーマやアクションを認識していない場合でもメッセージを受信できます。このため、ルーティング サービスは、ルーティングされる基盤のメッセージの詳細構成を追加することなく、メッセージをジェネリックにルーティングできます。  
  
## ルーティング コントラクト  
 ルーティング サービスには汎用 WCF メッセージ オブジェクトを使用できるため、コントラクトを選ぶ場合の最大の検討事項は、クライアントとサービスとの通信時に使用されるチャネルの形状です。ルーティング サービスは、メッセージを処理するときに対象型メッセージ ポンプを使用するため、通常、受信コントラクトの形状は、送信コントラクトの形状と一致します。ただし、サービス モデルのディスパッチャーがこの形状を変更する場合があります。たとえば、ディスパッチャーは、二重チャネルを要求\/応答チャネルに変換したり、セッションのサポートが不要で使用されていない場合に、このサポートを削除 \(つまり、**SessionMode.Allowed** が設定されている場合に、**IInputSessionChannel** を **IInputChannel** に変更\) したりします。  
  
 これらのメッセージ ポンプをサポートするために、ルーティング サービスでは、<xref:System.ServiceModel.Routing> 名前空間にコントラクトを用意しています。これらのコントラクトは、ルーティング サービスが使用するサービス エンドポイントを定義するときに、使用される必要があります。これらのコントラクトは型指定されていないため、どのようなメッセージの種類やアクションでも受信でき、ルーティング サービスは、特定のメッセージ スキーマを認識しない場合でもメッセージを処理できます。ルーティング サービスが使用するコントラクトの詳細については、「[Routing Contracts](../../../../docs/framework/wcf/feature-details/routing-contracts.md)」を参照してください。  
  
 ルーティング サービスによって提供されるコントラクトは、<xref:System.ServiceModel.Routing> 名前空間に含まれています。これらのコントラクトは、次の表のとおりです。  
  
|コントラクト|\[図形\]|チャネル形状|  
|------------|------------|------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode \= SessionMode.Allowed<br /><br /> AsyncPattern \= true<br /><br /> IsOneWay \= true|IInputChannel \-\> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode \= SessionMode.Required<br /><br /> AsyncPattern \= true<br /><br /> IsOneWay \= true|IInputSessionChannel \-\> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode \= SessionMode.Allowed<br /><br /> AsyncPattern \= true|IReplyChannel \-\> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode\=SessionMode.Required<br /><br /> CallbackContract\=typeof\(ISimplexSession\)<br /><br /> AsyncPattern \= true<br /><br /> IsOneWay \= true<br /><br /> TransactionFlow\(TransactionFlowOption.Allowed\)|IDuplexSessionChannel \-\> IDuplexSessionChannel|  
  
## 参照  
 [Routing Service](http://msdn.microsoft.com/ja-jp/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)   
 [ルーティングの概要](../../../../docs/framework/wcf/feature-details/routing-introduction.md)