---
title: "AJAX の統合と JSON のサポート | Microsoft Docs"
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
  - "AJAX の統合と JSON のサポート [WCF]"
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# AJAX の統合と JSON のサポート
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] が ASP.NET AJAX \(Asynchronous JavaScript and XML\) と JSON \(JavaScript Object Notation\) データ形式をサポートするため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは AJAX クライアントに操作を公開できます。AJAX クライアントは、JavaScript コードを実行し、HTTP 要求を使用してこのような [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにアクセスする Web ページです。このセクションのトピックでは、このサポートと実装方法について説明します。  
  
 ASP.NET AJAX とその ASP.NET 2.0 との統合[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ASP.NET AJAX の概要](http://go.microsoft.com/fwlink/?LinkId=96725)」を参照してください。  
  
## このセクションの内容  
 [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 構成によって、または、自動的に AJAX エンドポイントを構成するサービス ホストを生成するようにカスタマイズされたサービス ホスト ファクトリを使用することによって適切な AJAX エンドポイントを追加することで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを AJAX クライアントに公開する方法について説明します。  
  
 [ASP.NET を使用せずに WCF AJAX サービスを作成する方法](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 ASP.NET を使用しないで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成する方法について説明します。  
  
 [JSON などのデータ転送形式のサポート](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 ASP.NET AJAX サービスとのメッセージングで、XML の代わりに一般に使用される JSON 形式のサポートについて説明します。  
  
 [方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 AJAX 対応の ASP.NET Web サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web サービスに移行する方法について説明します。  
  
## 参照  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>   
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)