---
title: "方法: エンティティを追加、変更、および削除する (WCF Data Services) | Microsoft Docs"
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
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: エンティティを追加、変更、および削除する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリでは、<xref:System.Data.Services.Client.DataServiceContext> のオブジェクトで同等のアクションを実行して、データ サービスのエンティティ データを作成、更新、および削除できます。  詳細については、「[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例では、新しいオブジェクト インスタンスを作成し、<xref:System.Data.Services.Client.DataServiceContext> で <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> メソッドを呼び出してコンテキスト内に項目を作成します。  <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されたときに HTTP POST メッセージがデータ サービスに送信されます。  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## 使用例  
 次の例では、既存のオブジェクトを取得および変更してから、<xref:System.Data.Services.Client.DataServiceContext> で <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> メソッドを呼び出してコンテキスト内の項目を更新済みとしてマークします。  <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されたとき HTTP MERGE メッセージがデータ サービスに送信されます。  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## 使用例  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext> で <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> メソッドを呼び出して、コンテキスト内の項目を Deleted とマークします。  <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されたとき HTTP DELETE メッセージがデータ サービスに送信されます。  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## 使用例  
 次の例では、新しいオブジェクト インスタンスを作成し、<xref:System.Data.Services.Client.DataServiceContext> で <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> メソッドを呼び出して、関連する注文へのリンクと共に、コンテキスト内に項目を作成します。  <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されたときに HTTP POST メッセージがデータ サービスに送信されます。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [方法: 既存のエンティティを DataServiceContext にアタッチする](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)   
 [方法: エンティティ リレーションシップを定義する](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)   
 [バッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)