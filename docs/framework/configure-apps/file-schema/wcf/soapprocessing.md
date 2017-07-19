---
title: "&lt;soapProcessing&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;soapProcessing&gt;
異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。  
  
## 構文  
  
```  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|要素|説明|  
|--------|--------|  
|processMessages|SOAP メッセージ バージョン間のメッセージをマーシャリングするかどうかを指定するブール値。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。|  
  
## 解説  
 SOAP 処理は、メッセージ バージョン間でメッセージが変換されるプロセスです。  
  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ルーティング サービスは、あるプロトコルから別のプロトコルにメッセージを変換できます。  受信メッセージのバージョンと送信メッセージのバージョンが異なる場合、新しいメッセージが正しいバージョンで作成されます。  受信 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージの本文および関連するヘッダーが含まれた新しい [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージを作成することで、ある <xref:System.ServiceModel.Channel.MessageVersion> から別のメッセージ バージョンへのメッセージの変換が完了します。  アドレス指定に固有のヘッダーまたはルーター レベルで認識されるヘッダーは、新しい WCF メッセージの作成に使用されません。これらのヘッダーは、異なるバージョンであるか \(アドレス指定ヘッダーの場合\)、クライアントとルーターの間の通信の一部として処理されているためです。  
  
 発信メッセージにヘッダーが配置されるかどうかは、受信チャネル層を介して渡されたと認識されるようにマークされているかどうかによって決まります。  認識されないヘッダー \(カスタム ヘッダーなど\) は削除されずに送信メッセージにコピーされ、ルーティング サービスを介して渡されます。  メッセージの本文は、送信メッセージにコピーされます。  そして、メッセージは送信チャネルに送信されます。この時点で、すべてのヘッダー、および使用されている通信プロトコル\/トランスポートに固有のエンベロープ データが作成され、追加されます。  
  
 このような処理手順は、SOAP 処理動作が指定されているときに行われます。  この [\<soapProcessingExtension\>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) 動作は、ルーティング サービスが開始されたときに、すべてのクライアント \(送信\) エンドポイントに適用されるエンドポイントの動作です。  既定では、[\<routing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) 動作によって、クライアント エンドポイントごとに `processMessages` が `true` に設定された新しい [\<soapProcessingExtension\>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) 動作が作成およびアタッチされます。  ルーティング サービスが認識しないプロトコルを使用している場合や既定の処理動作をオーバーライドする場合は、ルーティング サービス全体または特定のエンドポイントにおいて SOAP 処理を無効にできます。すべてのエンドポイントのルーティング サービス全体で SOAP 処理を無効にするには、[\<routing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) 動作の `soapProcessing` 属性を `false` に設定します。  特定のエンドポイントで SOAP 処理を無効にするには、この動作を使用して `processMessages` 属性を `false` に設定してから、既定の処理コードを実行しないエンドポイントにこの動作をアタッチします。[\<routing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) 動作がルーティング サービスを設定するときには、サービスが既に存在しているため、エンドポイントの動作の再適用はスキップされます。  
  
## 参照  
 <xref:System.ServiceModel.Routing.Configuration.> SoapProcessingExtensionElement?qualifyHint=False&autoUpgrade=True   
 <xref:System.ServiceModel.Routing.SoapProcessingBehavior>