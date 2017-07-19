---
title: "方法: 既存のエンティティを DataServiceContext にアタッチする (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 変更 (データを)"
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: 既存のエンティティを DataServiceContext にアタッチする (WCF Data Services)
データ サービスにエンティティが既に存在する場合、クエリを最初に実行することなく、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用して、エンティティを表すオブジェクトを <xref:System.Data.Services.Client.DataServiceContext> に直接アタッチできます。  詳細については、「[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例は、データ サービスに保存する変更を含む既存の `Customer` オブジェクトを作成する方法を示します。  オブジェクトがコンテキストにアタッチされ、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出される前に、<xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> メソッドが呼び出されてアタッチされたオブジェクトが <xref:System.Data.Services.Client.EntityStates> としてマークされます。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)