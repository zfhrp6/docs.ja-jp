---
title: "MSMQ 統合のトランスポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# MSMQ 統合のトランスポート
ここでは、MSMQ 統合トランスポートによって生成されるすべての例外を示します。  
  
## 例外の一覧  
  
|リソース コード|リソースの文字列|  
|--------------|--------------|  
|MessageSizeMustBeInIntegerRange|このファクトリはメッセージをバッファーするため、メッセージ サイズは整数値の範囲内である必要があります。|  
|MsmqByteArrayBodyExpected|指定されたシリアル化形式と MSMQ メッセージの間で不整合が検出されました。メッセージを送受信できません。シリアル化形式 ByteArray では、MSMQ メッセージの本文が byte\[\] の種類でなければなりません。|  
|MsmqCannotDeserializeActiveXMessage|ActiveX のシリアル化中に、エラーが発生しました。メッセージを送受信できません。本文に指定されたバリアント型は、実際の MSMQ メッセージ本文と一致しません。|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|メッセージのプロパティが整合していません。メッセージを送受信できません。シリアル化の形式として ActiveX が使用されている場合は、BodyType メッセージ プロパティを指定できません。|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|MsmqIntegrationBinding の検証が失敗しました。サービス エンドポイントを開始できません。指定したバインディングは、指定したコントラクトの指定したサービス操作に対してメソッド署名をサポートしていません。MsmqIntegrationBinding を使用するよう、サービス操作を修正してください。|  
|MsmqInvalidTypeDeserialization|シリアル化の形式を認識できないため、ActiveX のシリアル化が失敗しました。メッセージを送受信できません。|  
|MsmqInvalidTypeSerialization|バリアント型を認識できません。ActiveX のシリアル化が失敗しました。メッセージを送受信できません。指定されたバリアント型はサポートされていません。|  
|MsmqStreamBodyExpected|シリアル化形式と本文のコンテンツの間で不整合があります。メッセージを送受信できません。ストリーム シリアル化モードを使用して送受信できるのは、ストリーム型の本文に限られます。|