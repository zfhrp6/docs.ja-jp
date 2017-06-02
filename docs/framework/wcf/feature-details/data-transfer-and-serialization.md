---
title: "データ転送とシリアル化 | Microsoft Docs"
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
  - "データ シリアル化 [WCF]"
  - "データ転送 [WCF]"
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# データ転送とシリアル化
接続されたシステムでは、サービスとクライアントのタスクの実行は、データの交換に依存します。サービスやクライアントの開発者は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のデータ処理方法とデータのシリアル化を理解して、効果的で保守しやすいアプリケーションを作成する必要があります。  
  
## このセクションの内容  
 [サービス コントラクトでのデータ転送の指定](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 サービスでのデータ転送の基本的な概念について説明します。  
  
 [データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 データ コントラクトの定義と、その作成方法と使用方法について説明します。  
  
 [データ コントラクト シリアライザー](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <xref:System.Runtime.Serialization.DataContractSerializer> クラス、または <xref:System.Runtime.Serialization.XmlObjectSerializer> クラスの拡張機能で、データのシリアル化を実行する方法について説明します。  
  
 [XmlSerializer クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <xref:System.Runtime.Serialization.DataContractSerializer> クラスの代わりに、<xref:System.Xml.Serialization.XmlSerializer> クラスを使う方法とその理由について説明します。  
  
 [メッセージ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 メッセージ コントラクトで SOAP メッセージを詳細に制御する方法について説明します。  
  
 [メッセージ クラスの使用](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 メッセージ クラス機能の使用方法について説明します。  
  
 [フィルター処理](../../../../docs/framework/wcf/feature-details/filtering.md)  
 各種の条件に基づいて、メッセージを事前処理できるフィルター処理について説明します。  
  
 [大規模データとストリーミング](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 バイナリ ファイルなど、大きなデータ ブロックを送信する方法について説明します。  
  
 [セキュリティに関するデータの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 データの転送とシリアル化をプログラムするときに注意する必要のある項目について説明します。  
  
 [データ転送のアーキテクチャの概要](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] におけるデータ転送の全般的な設計について説明します。  
  
## 関連項目  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## 関連項目  
 [エンコーダーとシリアライザーの拡張](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## 参照  
 [ベスト プラクティス : データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)   
 [サービスのバージョン管理](../../../../docs/framework/wcf/service-versioning.md)