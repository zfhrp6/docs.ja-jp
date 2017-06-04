---
title: "サービスおよびクライアントのセキュリティ保護 | Microsoft Docs"
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
  - "メッセージ セキュリティ [WCF]"
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# サービスおよびクライアントのセキュリティ保護
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でのセキュリティのプログラミングについて説明します。  一般に、これには、システムが提供する適切なバインディングを選択すること、セキュリティ要素のプロパティを適切に設定すること、サービス側\/クライアント側で使う資格情報の検索方法にまつわる、サービスの動作に関するプロパティを適切に設定することなどが含まれます。  これらの技術を知っていると、「[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)」に記載されているようなさまざまな状況で、セキュリティ要件に対処できます。  ただし、さらに高度な対策が必要な場合は、最初に「[カスタム バインディングを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)」、次に「[セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)」を参照してください。  多様なクレームに対応するシステムを構築する場合 \(または、そのようなシステムと相互運用する場合\) は、「[承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)」の各トピックを参照してください。  
  
## このセクションの内容  
 [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 メッセージを保護するために使うプログラミング モデルの概要  
  
 [トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 トランスポート層を介してやり取りするメッセージを保護する方法の概要  
  
 [メッセージのセキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメッセージ レベル セキュリティを使用する理由の要約  
  
 [セキュリティで保護されたセッション](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セッションのセキュリティを保護する際の考慮事項  
  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 X.509 証明書を使用する際に必要となる主な作業の解説  
  
## 関連項目  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## 関連項目  
 [セキュリティの概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [カスタム バインディングを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## 参照  
 [基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)