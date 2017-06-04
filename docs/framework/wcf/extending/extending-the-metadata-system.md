---
title: "メタデータ システムの拡張 | Microsoft Docs"
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
  - "メタデータの拡張 [WCF]"
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# メタデータ システムの拡張
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメタデータ システムは複数のクラスのグループおよびインターフェイスで、サービス ベースのアプリケーションを実装するために必要なメタデータを表します。クラスを変更または拡張するか、WSDL \(Web サービス記述言語\) の拡張子やカスタム WS\-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート\/インポートするインターフェイスを実装して構成します。  
  
## このセクションの内容  
 [WCF 拡張に対するカスタム メタデータのエクスポート](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> インターフェイスを実装および使用して、カスタム ポリシー アサーションを WSDL ドキュメントに埋め込む方法を説明します。  
  
 [WCF 拡張に対するカスタム メタデータのインポート](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> インターフェイスを実装および使用して、WSDL ドキュメント内のカスタム ポリシー アサーションの読み取りや応答を行う方法を説明します。  
  
 [カスタム バインディングを介したメタデータの公開と取得](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 カスタム バインディングを介してメタデータを交換する方法について説明します。