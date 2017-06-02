---
title: "使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較
ASP.NET Web サービスは、HTTP 上で SOAP \(Simple Object Access Protocol\) を使用してメッセージを送受信するアプリケーションを構築するために開発されました。  メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージのシリアル化を容易にするツールも提供されています。  このテクノロジを使用すると、Web サービス記述言語 \(WSDL\) で Web サービスを記述するメタデータが自動で生成されます。また、WSDL から Web サービス用のクライアントを生成する別のツールも用意されています。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用すると、.NET Framework アプリケーションで他のソフトウェア エンティティとメッセージを交換できます。  既定では SOAP が使用されますが、任意の形式のメッセージを使用でき、任意のトランスポート プロトコルを使用してメッセージを伝達できます。  メッセージ構造は XML スキーマを使用して定義できます。また、.NET Framework オブジェクトに対するメッセージをシリアル化するさまざまなオプションがあります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用すると、このテクノロジで構築されたアプリケーションを WSDL で記述するメタデータが自動で生成されます。また、WSDL からこのようなアプリケーション用のクライアントを生成するツールも用意されています。  
  
 ASP.NET Web サービスでサポートされる標準については、「[ASP.NET を使用して作成された XML Web サービス](http://go.microsoft.com/fwlink/?LinkId=94872)」を参照してください。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされる標準の詳細な一覧については、「[システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。  
  
## 参照  
 [開発者の視点から見た ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)